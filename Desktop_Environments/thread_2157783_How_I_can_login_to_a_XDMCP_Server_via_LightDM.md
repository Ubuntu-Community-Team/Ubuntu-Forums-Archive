---
title: "How I can login to a XDMCP Server via LightDM"
date: 2013-06-26
forum: Desktop Environments
---

### Post by burner1980 on 2013-06-26
Hello Together,

XDMCP Server is running, but how I can Login? On my Client PC there is no Option to Login via XDMCP!

I use Ubuntu 12.04 with LightDM and Unity. On the Login Screen is no Option.

Can anyone help me, I look for hours, but found nothing!

best regards

Burner

---

### Post by Krytarik on 2013-06-27
Looks like these are the relevant keys for the client machine's "/etc/lightdm/lightdm.conf":
```
# Seat defaults
#
# xserver-allow-tcp = True if TCP/IP connections are allowed to this X server
# xdmcp-manager = XDMCP manager to connect to (implies xserver-allow-tcp=true)
# xdmcp-port = XDMCP UDP/IP port to communicate on
# xdmcp-key = Authentication key to use for XDM-AUTHENTICATION-1 (stored in keys.conf)

[...]

[SeatDefaults]
[...]
#xserver-allow-tcp=false
#xdmcp-manager=
#xdmcp-port=177
#xdmcp-key=
```
Source: "/usr/share/doc/lightdm/lightdm.conf.gz/lightdm.conf"

Btw, there is a related bug report:
[QUOTE=Robert Ancell]Note this bug is about making a greeter that can choose which server to use. To setup lightdm as an XDMCP client always connecting to the same server you can use:

```
[SeatDefaults]
xdmcp-manager=your.xdmcp.server
```[/QUOTE]
[https://bugs.launchpad.net/lightdm/+bug/723224](https://bugs.launchpad.net/lightdm/+bug/723224)

Regards.

---

