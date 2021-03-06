# iotor-config

> The Ano config (`.iotorrc`) reader and writer.

The config spec can be read [here](https://docs.google.com/document/d/1APq7oA9tNao1UYWyOm8dKqlRP2blVkROYLZ2fLIjtWc/).


## Install

```sh
$ npm install --save iotor-config
```


## Usage

#### .load(overwrites)

Loads the iotor configuration from the configuration files.

Configuration is overwritten (after camelcase normalisation) with `overwrites` argument.

This method overwrites following environment variables:

- `HTTP_PROXY` with `proxy` configuration variable
- `HTTPS_PROXY` with `https-proxy` configuration variable
- `NO_PROXY` with `no-proxy` configuration variable

It also clears `http_proxy`, `https_proxy`, and `no_proxy` environment variables.

To restore those variables you can use `restore` method.

#### restore()

Restores environment variables overwritten by `.load` method.

#### .toObject()

Returns a deep copy of the underlying configuration object.
The returned configuration is normalised.
The object keys will be camelCase.


#### #create(cwd)

Obtains a instance where `cwd` is the current working directory (defaults to `process.cwd`);

```js
var config = require('iotor-config').create();
// You can also specify a working directory
var config2 = require('iotor-config').create('./some/path');
```

#### #read(cwd, overrides)

Alias for:

```js
var configObject = (new Config(cwd)).load(overrides).toJson();
```

## License

Released under the [MIT License](http://www.opensource.org/licenses/mit-license.php).
