---
title: "Compiz crashes - restores but with errors"
date: 2014-06-02
forum: Desktop Environments
---

### Post by MeanRoy on 2014-06-02
Background:
I ran 10.04 for a looong time, ever since it came out with only one problem and that was caused by a power failure.
In fact I can't recall a single crash!
After my many problems with 10.04 and kompozer I upgraded to 12.10.
I have been using it now for a couple of weeks, Kompozer works, Amaya works, Bluefish works.

Problem:
Today, when I opened Firefox the Firefox window was filled with special chars and symbols.
I re-booted. Firefox came up ok. After about 2-3 minutes, I got a message that compiz had crashed. I let it send off a crash report and clicked on re-start.
Crashed again, sent another report, rinse and repeat.

I re-booted, Same thing.
After much searching I found the procedure to reset unity in 12.10 quantel on ubuntuguide.net.

I performed the required steps in a terminal (compiz crashed again while I was working in the terminal window)

I got this, after which I re-booted. seems to be working but what is going on!:
```
[INDENT][INDENT]meanroy@meanroy-desktop:~$ sudo apt-get install dconf-tools
Reading package lists... Done
Building dependency tree
Reading state information... Done
dconf-tools is already the newest version.
dconf-tools set to manually installed.
The following packages were automatically installed and are no longer required:
  compiz-plugins-extra compiz-plugins-main hyphen-en-us kdesudo
  libreoffice-help-en-gb libreoffice-l10n-en-gb libreoffice-l10n-en-za
  mythes-en-us ubuntu-release-upgrader-qt update-manager-kde
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
meanroy@meanroy-desktop:~$ sudo dconf reset -f /org/compiz/
meanroy@meanroy-desktop:~$ setsid unity
meanroy@meanroy-desktop:~$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (expo) - Warn: failed to bind image to texture
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2014-06-02 16:19:59 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2014-06-02 16:19:59 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2014-06-02 16:19:59 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2014-06-02 16:20:00 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window54525992
WARN  2014-06-02 16:20:00 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window54525992
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.threshold
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.timeout
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.threshold
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.timeout
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.threshold
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.timeout
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.threshold
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.timeout
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.threshold
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.timeout
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.threshold
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.timeout
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.threshold
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.timeout
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.threshold
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.timeout
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.threshold
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.drag.timeout
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.threshold
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.pinch.timeout
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.threshold
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.tap.timeout
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.threshold
ERROR 2014-06-02 16:20:00 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.timeout
WARN  2014-06-02 16:20:00 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window54525992
WARN  2014-06-02 16:20:00 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window54525992
WARN  2014-06-02 16:20:00 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window54525992
WARN  2014-06-02 16:20:00 unity <unknown>:0 Failed to fetch boolean: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window54525992
WARN  2014-06-02 16:20:42 unity.glib.dbusproxy GLibDBusProxy.cpp:291 Calling method "InfoRequest" on object path: "/net/launchpad/lens/photos" failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.Unity.Lens' on object at path /net/launchpad/lens/photos
WARN  2014-06-02 16:20:42 unity.glib.dbusproxy GLibDBusProxy.cpp:291 Calling method "SetViewType" on object path: "/net/launchpad/lens/photos" failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.Unity.Lens' on object at path /net/launchpad/lens/photos
[/INDENT]
[/INDENT]

```

---

### Post by monkeybrain20122 on 2014-06-03
12.10 has reached end of life in April, I doubt that there is any point in trying to fix an end of life OS, please install a supported version of Ubuntu, either 12.04 or 14.04 (13.10 will reach end of life in mid (?) July so there is no point to install it either)

And please don't "upgrade", backup your data and do a clean install, I suspect many of your current problems are the result of 'upgrade'.

---

### Post by MeanRoy on 2014-06-03
OK, I'll try that. I upgraded to 12.10 from 10.04 and didn't realize 12.10 was already at end of life.
I'm going to go directly to 14.04 LTS.

*wish me luck*
Ha ha ... so much for luck!
Loading up ok now that I've replaced my DVD drive, explains why I wasn't able to use system rescue!

---

### Post by MeanRoy on 2014-06-03
OK, it's installing, I've decided to install along side 12.10 because I wasn't able to back up recent work and I'd rather not lose it.

---

### Post by MeanRoy on 2014-06-03
OK, it's installed.
Sure takes a long time to boot!
Whats with the Amazon thing, we have commercials now?
Interesting, I click on the Amazon icon to check it out, a window advertising stuff comes up.
OK, I click on the red x (upper left corner) to close the window, nothing happens, click a couple of more times, mouse cursor goes away.
Humm, this is not good. Try ctl-alt-T, nothing, no terminal.
System appears frozen.

Damn! Hard re-boot.
OK, what appears to be the grub menu appears, but am unable to select anything, the curser keys don't have any effect.
Boots into 14.04.
OK, mouse curser is back. I'll start with system settings and see if I can shrink those humongous icons.
Ok, that worked, nice to see icon size is more adjustable than previously.
[INDENT]> Checking other options I see I can choose to use the NVIDIA Binary driver for my GeForce 9800GTX+ if desired but I'm not changing it now.
 (thank you very much)
Firefox comes up, but a different version and I see they have found new ways to hide things again. Awkward. Gee all I wanted to do was set the home page. This is ridiculous, I can't even find the 'About' to see what ver. it is. OK, I searched for Firefox and find it a * ver 28 build 2* yada yada yada. Ok, turned on the bookmarks and  loaded up the "getting started with Firefox", I see I have to go to the site and drag it to the icon, OK. Funny but the version installed has no File Edit View History etc. Wonder where that is. Something to deal with later

[/INDENT]

OK, thanks for the advise, now I have to try to find out what to do about the problems, Grub doesn't select, no menus in Firefox etc, and install the programs I need. ( Probably around 40 hours for installs alone.)
Oh, and stuff like Tomboy notes which can't be imported apparently, not to mention mail, not quite sure what I can do about that!

Roy

*[SIZE=1](and then, of course working with a desktop that thinks it's my smartphone)[/SIZE]*

---

