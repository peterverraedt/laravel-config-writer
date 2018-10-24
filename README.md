# Laravel Config Writer

Write to Laravel Config files and maintain file integrity.

This library is an extension of the Config component used by Laravel. It adds the ability to write to configuration files.

You can rewrite array values inside a basic configuration file that returns a single array definition (like a Laravel config file) whilst maintaining the file integrity, leaving comments and advanced settings intact.

The following value types are supported for writing: strings, integers, booleans and single-dimension arrays.

Fork of `octobercms\laravel-config-writer`.

## Support

This provider is designed to be used in Laravel from `5.4` version.

## Usage

Install through composer:
```
composer require "tekreme73/laravel-config-writer"
```

### Standard usage

Add this to `app/config/app.php` under the 'providers' key:

```php
Tekreme73\Laravel\ConfigWriter\ConfigServiceProvider::class,
```

You can now write to config files:

```php
Config::write('app.url', 'http://domain.com');

app('config')->write(['app.url' => 'http://domain.com']);
```

### Outside Laravel

The `Rewrite` class can be used anywhere.

```php
$writeConfig = new Tekreme73\Laravel\ConfigWriter\Rewrite;
$writeConfig->toFile('path/to/config.php', [
    'item' => 'new value',
    'nested.config.item' => 'value',
    'arrayItem' => ['Single', 'Level', 'Array', 'Values'],
    'numberItem' => 3,
    'booleanItem' => true
]);
```
