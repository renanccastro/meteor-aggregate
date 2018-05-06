[![](https://api.travis-ci.org/meteorhacks/meteor-aggregate.svg)](https://travis-ci.org/meteorhacks/meteor-aggregate)

# maintained fork of meteorhacks:aggregate

A simple package to add proper aggregation support for Meteor. This package exposes `.aggregate` method on `Mongo.Collection` instances.

> this only works on server side and there is no oberserving support or reactivity built in

## Usage

Add to your app with
```
meteor add sakulstra:aggregate
```

Then simply use `.aggregate` function like below.

```js
var metrics = new Mongo.Collection('metrics');
var pipeline = [
  {$group: {_id: null, resTime: {$sum: "$resTime"}}}
];
var result = metrics.aggregate(pipeline);
```

### Using Options

~~~js
var result = new Mongo.Collection('metrics');
var metrics = new Mongo.Collection('metrics');
var pipeline = [
  {$group: {_id: null, resTime: {$sum: "$resTime"}}}
];
var result = metrics.aggregate(pipeline, {explain: true});
console.log("Explain Report:", JSON.stringify(result[0]), null, 2);
~~~

## Why?

There are few other aggregation packages out there. All of them written with some complex hacks and there are some easy way to do things.
They also don't work with custom Mongo drivers as well.

And this package is short and simple. (~20 LOC)


## What the fork?!
meteorhacks/meteor-aggregate seems pretty unmaintained, which is sad :/
Meteor 1.7 and it's upgrade to mongodriver v3 introduced some breaking changes
I want to incorporate https://github.com/meteorhacks/meteor-aggregate/pull/41/files