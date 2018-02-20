# OCF Resource agent of PPP Connection

## Example

Here is an example that connect `dsl-provider`

```
primitive ppp-myisp PPPConnection \
        params isp=dsl-provider \
        op monitor interval=30 timeout=10 on-fail=restart \
        op start timeout=60 interval=0 on-fail=restart \
        op stop timeout=60 interval=0
```

## Option parameters

* **isp** - ISP name to connect. This will be passed to pon/poff, and pppd will be monitored with specified isp. Default is `provider`.
* **expected_ip4** - Expected IPv4 address for the ppp connection. If you specify this parameter, startup and monitor proecesses will wait the address associated with ppp interface.
* **expected_ip6** - Expected IPv6 local address (same as v4).
* **ip_wait_sec** - Resource will wait specified seconds for ppp interface aquires expected IP address provided by `expected_ip4` or `expected_ip6`. Default is 30.
* **pon_retries** - Retry limit for pon. Default is 30.
* **pon_wait_sec** - Resource will wait specified seconds for ppp connection up. When it's exceeded, retry to run pon.
* **poff_wait_sec** - Resource will wait specified seconds for ppp connection down. When it's exceeded, retry to run poff.

## License/Copyright

This script has been distributed under GNU General Public License version 2 (GPL2).

Copyright (c) 2017 Tatsuki Sugiura <sugi@nemui.org> and OSDN Corporation <tech@osdn.jp>.


