<table width="100%">
	<tr>
		<td align="left" width="70">
			<strong>WP Redis - Predis Client</strong><br />
            An alternative Redis client for use with <a href="https://github.com/pantheon-systems/wp-redis">WP Redis</a>.
		</td>
		<td align="right" width="20%">
			<a href="https://travis-ci.org/humanmade/wp-redis-predis-client">
				<img src="https://travis-ci.org/humanmade/wp-redis-predis-client.svg?branch=master" alt="Build status">
			</a>
            <a href="https://codecov.io/gh/humanmade/wp-redis-predis-client">
            <img src="https://codecov.io/gh/humanmade/wp-redis-predis-client/branch/master/graph/badge.svg" alt="Codecov" />
            </a>
		</td>
	</tr>
	<tr>
		<td>
			A <strong><a href="https://hmn.md/">Human Made</a></strong> project. Maintained by @nathanielks.
		</td>
		<td align="center">
			<img src="https://hmn.md/content/themes/hmnmd/assets/images/hm-logo.svg" width="100" />
		</td>
	</tr>
</table>

# WP Redis - Predis Client

This is a package that enables the use of [Predis](https://github.com/nrk/predis/) as a Redis Client as opposed to PHPRedis for [WP Redis](https://github.com/pantheon-systems/wp-redis/). Predis has the distinct advantage of connecting to Redis via TLS, encrypting traffic in-transit. Requires WP Redis >= 0.7.0.

## Getting Started

### Requiring Files
#### Composer

When using Composer, `functions.php` file will automatically be loaded whenever you include Composer's autoloader in your project.

#### Manually Requiring

The only file needing `require_once`ing for WP Predis to work correctly is `functions.php`. Clone this repo somewhere in your project and include `functions.php` somewhere early (such as `wp-config.php`):

```
require_once '/path/to/wp-redis-predis-client/functions.php';
```

### Object Cache stub


Now that files have been included, it's recommended you use the included [`object-cache.php`](object-cache.php) file instead of the one included with WP Redis. It will add the required filters for WP Predis to work and then include WP Redis' `object-cache.php` file. Once `object-cache.php` is in `wp-content` (or whatever content directory you are using), you're good to go!

### Configuring Predis

WP Redis - Predis Client adheres to WP Redis' [configuration details](https://github.com/pantheon-systems/wp-redis#installation). Predis also takes an additional argument, `ssl`, for configuring TLS connections. See PHP's [SSL Context options](http://php.net/manual/en/context.ssl.php) for more details.


```php
global $redis_server;
$redis_server = array(
    'host' => '127.0.0.1',
    'port' => 6379,
	'ssl'  => array(
		'local_cert' => '/path/to/certificate_and_key.pem',
		'verify_peer' => true,
	),
);
```


