---
title: "Overriding klocker screen with xscreensaver when clicking on lock screen button"
date: 2023-01-14
forum: Desktop Environments
---

### Post by jdabronx on 2023-01-14
I run xscreensaver and there used to be a way to override the default kscreenlocker so that when you click the 'lock screen' button, the xscreensaver kicks in vs. the default kscreensaver (which is pretty lame).

This used to work flawlessly in the past by:

    finding the kscreensaver_greet file (current version is located in /usr/lib/x86_64-linux-gnu/libexec/&#8203;)
    replacing the file with the following script[INDENT=2]#!/bin/sh
xscreensaver-command -lock&#8203;
[/INDENT]

    making xscreensaver-command executable via chmod a+x 


When I try this on my upgraded machine, I get a message that the "screen locker is broken and unlocking is not possible anymore"
In order to unlock, I need to switch to a virtual terminal and enter "loginctl unlock-session 3"

Also wanted to add that xscreensaver itself seems to be working fine and starts after the specified amount of inactivity

Instructions that have worked in the past => [https://manpages.ubuntu.com/manpages/xenial/man1/xscreensaver.1.html](https://manpages.ubuntu.com/manpages/xenial/man1/xscreensaver.1.html)

---

