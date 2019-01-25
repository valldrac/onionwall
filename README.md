OnionWall
=========

Portable router to provide anonymous access to Internet via Tor.

It minimizes the risk of being caught in case an attacker gets into your computer while you are browsing anonymously with [Tor Browser](https://www.torproject.org/projects/torbrowser.html.en). It also reduces the potential to make fatal mistakes; it enforces all Internet traffic to be sent over the Tor Network.

OnionWall is the hardware alternative to the operating systems focused on anonymity like [Tails](https://tails.boum.org/) or [Whonix](https://www.whonix.org/).

The firmware is based on latest [OpenWrt](https://openwrt.org/) LEDE 17.01.6.

![Overview](docs/images/overview.png)

## Overview

OnionWall provides 3 network interfaces:

* **TOR**: Ethernet network with Tor listening on static IP **10.0.0.1**. All the traffic must be explicitly proxied to the port **9050**. Built-in DNS forwarder is listening on port **53** as well.
* **LAN**: Ethernet network for administration purposes with DHCP server. The Web Admin GUI is https://192.168.8.1 default login: **_root_** password: **_goodlife_**. It also has a HTTP proxy listening on port **8081** with unrestricted Internet access, useful for logging into captive portals.
* **WWAN**: Wireless network with DHCP client. Typically connected to your Internet uplink.

## Quick Start Guide

* Purchase one of the [compatibles devices](#compatible-devices).
* Download the [latest firmware](https://gitlab.com/valldrac/onionwall/releases) and [flash it](https://gitlab.com/valldrac/onionwall/wikis/Flashing) onto the router.
* Connect your laptop to the LAN network and [configure the Internet uplink](https://gitlab.com/valldrac/onionwall/wikis/Setup-Wireless).
* Grab a dedicated laptop and remove or disable all radio devices (Wi-Fi and Bluetooth).
* Connect it to the TOR network and boot your preferred secure Linux distro.
* [Configure Tor Browser](https://gitlab.com/valldrac/onionwall/wikis/Configure-Tor-Browser).
* Enjoy!

## Compatible Devices

| Device Type | Brand | Model | CPU MHz | CPU Cores | Flash MB | RAM MB | WLAN 2.4GHz | WLAN 5.0GHz | Snapshot Build |
|-------------|-------|-------|---------|-----------|----------|--------|-------------|-------------|----------------|
| Wi-Fi Router | GL.iNet | [GL-AR150](http://www.gl-inet.com/ar150/) | 400 | 1 | 16 | 64 | b/g/n | - | [Browse](https://gitlab.com/valldrac/onionwall/-/jobs/artifacts/master/browse/?job=gl-ar150) |

## Development

If you are interested in developing  or **building your own firmware**, try out the vagrant setup https://gitlab.com/valldrac/onionwall-vagrant. Your contributions are always welcome!

To make it easier, you can check the changes made versus the stock LEDE firmware: https://gitlab.com/valldrac/onionwall/compare/lede-17.01.6...master

For more detailed information please visit the [Wiki](https://gitlab.com/valldrac/onionwall/wikis).

## Security

To ensure security, OnionWall completely disables packet forwarding and applies strict set of firewall rules to each zone. TorPort is the only open port in the TOR network, so administration must be performed on a separate channel from the proxied computers.

It encourages the use of a dedicated PC without Wi-Fi to prevent malware from scanning nearby wireless networks and geolocating your position.

OnionWall is not a transparent proxy for [good reasons](https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy#WARNING).

## Fingerprint

OnionWall was developed to keep to a minimum the specificities that could be used to determine whether a particular user is running it or not.

In particular, it **spoofs the MAC address** of the wireless chipset at kernel level on every boot.

## Bugs

Never detach the antenna of the GL-AR150 when powered-on. It will damage the wireless chipset.

Report bugs to [Issues](https://gitlab.com/valldrac/onionwall/issues).

## Credits

Original idea by grugq's [portal](https://github.com/grugq/portal).

## Disclaimer

This project is NOT sponsored by The Tor Project. Use at your own risk.
