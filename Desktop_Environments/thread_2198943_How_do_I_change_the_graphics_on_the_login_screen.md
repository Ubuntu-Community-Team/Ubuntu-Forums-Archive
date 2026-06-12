---
title: "How do I change the graphics on the login screen?"
date: 2014-01-11
forum: Desktop Environments
---

### Post by PopsTheSailor on 2014-01-11
I installed some "stuff" trying to fix my external audio and when I rebooted, the graphics on the login screen changed. I've searched and can't find any info on how to change the graphics. I can find plenty on how to change the background image but that's now what I need to do. When I say "graphics" I'm referring to things like the user list, how the fields look where you enter your password. That stuff.

Any idea how I change it to the system default look and feel?

---

### Post by Rex Bouwense on 2014-01-11
Look here 
[https://wiki.ubuntu.com/LightDM#Change_the_wallpaper](https://wiki.ubuntu.com/LightDM#Change_the_wallpaper)

---

### Post by Dennis N on 2014-01-11
Perhaps the greeter theme has changed. The configuration of the lightdm greeter is located at:

[FONT=Courier New]**/etc/lightdm/lightdm-gtk-greeter.conf**[/FONT]
(actually a symlink to the real configuration file)

Check if the theme-name, icon-theme-name, and font-name are correct: **Lubuntu-default, lubuntu, Ubuntu**
My reference is Lubuntu 13.04. This configuration may be different with other releases. Some settings here seem be inactive.

(logo setting for example may not work. logo is set to computer, but uses the user-supplied **~/.face** file.)

---

### Post by PopsTheSailor on 2014-01-13
I looked in the /etc/lightdm/ location and have 5 files listed below

10-ubuntu.conf
50-guest-wrapper.conf  
50-xserver-command.conf
50-greeter-wrapper.conf  
50-unity-greeter.conf

The contents of 50-gretter-wrapper.conf are:

[SeatDefaults]
greeter-wrapper=/usr/lib/lightdm/lightdm-greeter-session

Here is the contents of the /usr/lib/lightdm/lightdm-gretter-session

#!/bin/sh
# -*- Mode: sh; indent-tabs-mode: nil; tab-width: 4 -*-
#
# Copyright (C) 2011 Canonical Ltd
# Author: Michael Terry <michael.terry@canonical.com>
#
# This program is free software: you can redistribute it and/or modify it under
# the terms of the GNU General Public License as published by the Free Software
# Foundation, version 3 of the License.
#
# See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) the full text of the license.

# This wrapper merely ensures that dbus-daemon lives only as long as this
# script does.  Otherwise, it's very easy for dbus-daemon to be autolaunched
# and detached from the greeter.

trap cleanup TERM EXIT

cleanup()
{
    trap - TERM EXIT
    if [ -n "$DBUS_SESSION_BUS_PID" ]; then
        kill "$DBUS_SESSION_BUS_PID"
    fi
    if [ -n "$CMD_PID" ]; then
        kill "$CMD_PID"
    fi
    exit 0
}

eval `dbus-launch --sh-syntax`

exec $@ &
CMD_PID=$!
wait $CMD_PID
CMD_PID=

Not sure where I go from here......................

---

