---
title: "Alt+F2 doesn't work!!!!! Gnome-settings-daemon?"
date: 2006-12-12
forum: Desktop Environments
---

### Post by jaywhy13 on 2006-12-12
Because I keep on getting this error... Alt+F2 doesn't work... some of my coammands that use up Super in Beryl don't work either. The same thing happens in the plain ol gnome session. The error is:
```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

GNOME will still try to restart the Settings Daemon next time you log in.
```
I get that when gnome starts up... PLZ HELP!!!!!!!!!!!!!

---

### Post by jaywhy13 on 2006-12-12
When I try to manually start gnome from the konsole I get....
!!"""""xrdb:  "*Label.background" on line 243 overrides entry on line 170
xrdb:  "*Text.background" on line 249 overrides entry on line 211
xrdb:  "*Label.foreground" on line 255 overrides entry on line 171
xrdb:  "*Text.foreground" on line 261 overrides entry on line 212
"[1165929474,000,xklavier.c:xkl_engine_start_listen/]   The backend does not require manual layout management - but it is provided by the applicationSegmentation fault
jay@s4b:~$ xrdb:  "*Label.background" on line 243 overrides entry on line 170
xrdb:  "*Text.background" on line 249 overrides entry on line 211
xrdb:  "*Label.foreground" on line 255 overrides entry on line 171
xrdb:  "*Text.foreground" on line 261 overrides entry on line 212
xrdb:  "*Label.background" on line 243 overrides entry on line 170
xrdb:  "*Text.background" on line 249 overrides entry on line 211
xrdb:  "*Label.foreground" on line 255 overrides entry on line 171
xrdb:  "*Text.foreground" on line 261 overrides entry on line 212

---

### Post by auburn on 2006-12-14
see if this helps:
[https://launchpad.net/distros/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/distros/ubuntu/+source/control-center/+bug/61381)

---

