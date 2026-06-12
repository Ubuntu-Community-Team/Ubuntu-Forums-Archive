---
title: "Plasma 5.18.8 bugs"
date: 2022-08-08
forum: Desktop Environments
---

### Post by nibal on 2022-08-08
Hi,

Had to reinstall Ubuntu 20.04 and plasma, after my main hard disk crashed.
I don't remember having so many problems with Plasma the first time:(
Seems, I cannot set a desktop wallpaper now. I just get a pitch black background:(
Besides it is very difficult to configure plasma, since all configuration is all dark and unreadable:(

Any ideas how to fix this?

TIA
Nikos[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290823&stc=1[/IMG]

---

### Post by guiverc on 2022-08-08
I wonder if you've restored configuration from a backup? and thus your configuration has set defaults to packages/themes you don't have installed?

Please note I'm only guessing, and don't have a 20.04 system handy to look, but maybe look in ~/.config/kdedefaults & other config type files, especially if you've restored your configuration and not re-created it from scratch using options that you have installed.  (*given it's dark you show, you didn't have dark configured using  kvantum etc but your new system doesn't have it installed etc*)

---

### Post by nibal on 2022-08-08
> **guiverc said:**
> I wonder if you've restored configuration from a backup? and thus your configuration has set defaults to packages/themes you don't have installed?

Please note I'm only guessing, and don't have a 20.04 system handy to look, but maybe look in ~/.config/kdedefaults & other config type files, especially if you've restored your configuration and not re-created it from scratch using options that you have installed.  (*given it's dark you show, you didn't have dark configured using  kvantum etc but your new system doesn't have it installed etc*)

You are absolutely right. I restored my home directory from backup.
In that case, shouldn't there be an error in syslog?
I'll check my .config...

---

### Post by nibal on 2022-08-09
I tried moving the .config, .local and .kde dirs.
No joy:(
If anyone knows of a more specific setting affecting this, it would be very helpful:)

---

### Post by nibal on 2022-08-09
Unfortunately it is not a user or configuration issue:(
I even moved to a minimal home with just the bare essentials:
.profile, .bashrc & ,bash_profile
Same behavior: Erratic plasma, with all options & Desktop blackened out,
and windows just appearing at random at various workspaces:(
I reinstalled all packages again:
sudo apt install kde-full
sudo apt install kde-standard
sudo apt install kde-plasma-desktop

Using Ubuntu 20.04.
Last time I tried the exact same thing, plasma worked like a charm:)
What is going on here? Forum requires reauthenticating every 2' to posr a reply with a correction:( Please fix!

---

### Post by nibal on 2022-08-09
Upon further inspection, I find these errors in my .xsession-errors:

 kdeinit5: preparing to launch 'libkdeinit5_kded5'Could not open kded5 using a library: Cannot load library libkdeinit5_kded5: (libkdeinit5_kded5: cannot open shared object file: No such file or directory)
I couldn;t find it in my system. It exists for bionic (18.04) not foccal. Is it required? Should I go and fetch it?

A little further along:

org.kde.libkbolt: Failed to connect to Bolt manager DBus interface:.
org.kde.bolt.kded: Couldn't connect to Bolt DBus daemon
kdeinit5: PID 1379 terminated.
xsettingsd: Couldn't find config file. Tried the following:

And journalctl shows a bunch of undefined errors:

ug 08 07:03:18 DrWho org.kde.LogoutPrompt[4003]: file:///usr/share/plasma/look-and-feel/org.kde.breeze.desktop/contents/components/UserDelegate.qml:41: ReferenceError: config is not defined
Aug 08 07:03:18 DrWho org.kde.LogoutPrompt[4003]: file:///usr/share/plasma/look-and-feel/org.kde.breeze.desktop/contents/components/UserDelegate.qml:34: ReferenceError: model is not defined
Aug 08 07:03:18 DrWho org.kde.LogoutPrompt[4003]: file:///usr/share/plasma/look-and-feel/org.kde.breeze.desktop/contents/components/ActionButton.qml: ReferenceError: config is not defined

..and 

..and X11 broken connections (looping many times):

Aug 07 22:40:53 DrWho org.freedesktop.impl.portal.desktop.kde[23322]: ICE default IO error handler doing an exit(), pid = 23322, errno = 32
Aug 07 23:13:07 DrWho org.freedesktop.impl.portal.desktop.kde[1454]: The X11 connection broke (error 1). Did the X11 server die?
Aug 07 23:26:02 DrWho xdg-desktop-por[1453]: xdg-desktop-portal-kde: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
Aug 08 03:41:46 DrWho org.kde.kdeconnect.daemon.desktop[1907]: ICE default IO error handler doing an exit(), pid = 1907, errno = 32
Aug 08 04:46:33 DrWho org.kde.KScreen[19292]: kscreen.xcb.helper: Event Error:  147
Aug 08 04:47:26 DrWho org.kde.kdeconnect.daemon.desktop[16213]: ICE default IO error handler doing an exit(), pid = 16213, errno = 32
Aug 08 04:47:26 DrWho org.kde.ActivityManager[19220]: The X11 connection broke (error 1). Did the X11 server die?
Aug 08 04:47:26 DrWho unknown[19264]: kded5: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


I will go searching the web about these, and will update here,
but if you have any ideas, plz share them:)

---

### Post by ActionParsnip on 2022-08-09
Are you using Wayland or Xorg? Maybe if you use Xorg (if you aren't already) then it'll be OK

---

### Post by nibal on 2022-08-09
The first error (ICE) was easy to fix just changed the mod of ~/.ICEautoeity to 666:
-rw-rw-rw- 1 user user 404150 Mar 20  2019 .ICEauthority
Simple enough. Couldn't plasma instalation handle it?

of the rest:
.xsession-errors (repeating many times):

[h264 @ 0x564551006dc0] Error splitting the input into NAL units.
avformat_open_input error:  -1094995529

These 2 seem to be resukt of the Xserver broken connections below.

journalctl errors (repeating every 30'):

ug 10 00:28:35 DrWho org.freedesktop.impl.portal.desktop.kde[1494]: The X11 connection broke (error 1). Did the X11 server die?
Aug 10 00:28:35 DrWho org.kde.kglobalaccel[1466]: The X11 connection broke (error 1). Did the X11 server die?
Aug 10 00:28:35 DrWho org.kde.runners.baloo[5014]: The X11 connection broke (error 1). Did the X11 server die?
Aug 10 00:28:35 DrWho org.kde.KScreen[1626]: The X11 connection broke (error 1). Did the X11 server die?
Aug 10 00:28:35 DrWho org.kde.ActivityManager[1578]: The X11 connection broke (error 1). Did the X11 server die?
Aug 10 00:34:07 DrWho org.kde.KScreen[1625]: kscreen.xcb.helper: Event Error:  147
Aug 10 00:47:45 DrWho org.kde.KScreen[1625]: The X11 connection broke (error 1). Did the X11 server die?
Aug 10 00:47:45 DrWho org.kde.kglobalaccel[1457]: The X11 connection broke (error 1). Did the X11 server die?
Aug 10 00:47:45 DrWho org.freedesktop.impl.portal.desktop.kde[1504]: The X11 connection broke (error 1). Did the X11 server die?
Aug 10 00:47:45 DrWho org.kde.ActivityManager[1566]: The X11 connection broke (error 1). Did the X11 server die?
Aug 10 00:52:37 DrWho org.kde.KScreen[1586]: kscreen.xcb.helper: Event Error:  147



I am not sure of these are due to rebooting the PC...

Plz fix the authentication timeout in the forum. Make it at least 30'.

---

### Post by nibal on 2022-08-09
This was a fresh install of Ubuntu 20.04.
It seems that plasma is vert buggy for Ubuntu...
I have wasted enough time with it:(
Time to ditch it and give Kubuntu a try...

---

