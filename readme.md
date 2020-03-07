# IPAddr

## Usage

```php
use Press\Utils\IPAddr;
use Press\Utils\IPAddr\IPv4;
use Press\Utils\IPAddr\IPv6;
```

### IPv4

```php
// convert IPV4 to `string`
$addr = new IPAddr\IPv4([192, 168, 1, 1]);
$addr->toString() === '192.168.1.1';


// kind for IPv4
$addr = new IPAddr\IPv4([1, 2, 3, 4]);
self::assertEquals($addr->kind(), 'ipv4');


// validates IPv4 address
IPv4::isValid('192.168.007.0xa') === true;
IPv4::isValid('1024.0.0.1') === false;
IPv4::isValid('8.0xa.wtf.6') === false;


// parse weird formats
IPv4::parse('192.168.1.1')->octets === [192, 168, 1, 1];
IPv4::parse('0xc0.168.1.1')->octets === [192, 168, 1, 1];
IPv4::parse('192.0250.1.1')->octets === [192, 168, 1, 1];
IPv4::parse('0xc0a80101')->octets === [192, 168, 1, 1];
IPv4::parse('030052000401')->octets) === [192, 168, 1, 1];
IPv4::parse('3232235777')->octets === [192, 168, 1, 1];
```

### IPv6

```php

// convert IPv6 to string
$addr = new IPv6([0x2001, 0xdb8, 0xf53a, 0, 0, 0, 0, 1]);
$addr->toNormalizedString() === '2001:db8:f53a:0:0:0:0:1';
$addr->toString() === '2001:db8:f53a::1';
(new IPv6([0, 0, 0, 0, 0, 0, 0, 1]))->toString() === '::1';
(new IPv6([0x2001, 0xdb8, 0, 0, 0, 0, 0, 0]))->toString() === '2001:db8::';


// kind for IPv6
$addr = new IPv6([0x2001, 0xdb8, 0xf53a, 0, 0, 0, 0, 1]);
$addr->kind() === 'ipv6';

```
