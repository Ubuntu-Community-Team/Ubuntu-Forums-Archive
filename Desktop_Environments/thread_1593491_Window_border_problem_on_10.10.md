---
title: "Window border problem on 10.10"
date: 2010-10-11
forum: Desktop Environments
---

### Post by ocardona on 2010-10-11
I was running 10.04 over freenx and updated to 10.10 over freenx.  After reboot the following window problem occurs.

When a window is instantiated, the borders take on the color of whatever the background is at the time.  Either desktop background or windows/contents in the background.  The window buttons also take on this behavior, there are not visible but do exist because I can close, maximize and roll up if I press on the expected button location.

I tried the following to no avail:
metacity --replace
compiz --replace
setting new themes, border, etc.

Please advise.....

---

### Post by ocardona on 2010-10-11
If I select KWin as the window manager the borders appear, though not with my font preferences.  However ifI switch back to Metacity of Compiz then they go away again.  If I leave the settings as KWin and reboot then it's back to the incorrect behavior....

---

### Post by bmelancon on 2010-10-13
> **ocardona said:**
> I was running 10.04 over freenx and updated to 10.10 over freenx.  After reboot the following window problem occurs.

When a window is instantiated, the borders take on the color of whatever the background is at the time.  Either desktop background or windows/contents in the background.  The window buttons also take on this behavior, there are not visible but do exist because I can close, maximize and roll up if I press on the expected button location.

I tried the following to no avail:
metacity --replace
compiz --replace
setting new themes, border, etc.

Please advise.....

I am experiencing the same behavior under the same circumstances when using NX.  


I'm providing some additional details in the hopes it will help someone figure this out.

Everything works fine when using the system normally, it's only under NX where this behavior shows up.  Everything was working perfectly under 10.04.  It appears to be some quirk in how NX works under 10.10.

"metacity --replace" does not fix the problem for me, but does sometimes make make random pixels show up in the window borders.

Dragging one window over another window makes blank borders appear on the lower windows.  None of the controls show up but they still work if you click the right spots.

KDE works under NX.  I don't typically use KDE and I have not checked if the fonts are different when using the computer locally.

---

### Post by crowba on 2010-10-19
Same problem here window boarders are not correct anymore with ubuntu 10.10 and freenx

[[IMG]http://img5.imagebanana.com/img/h053temb/thumb/Clipboard02.png[/IMG]]("http://www.imagebanana.com/view/h053temb/Clipboard02.png")

---

### Post by sylaan on 2010-10-27
I have the same problem, I use Nomachine's NX to log into a Ubuntu 10.10 and since the upgrade, windows decorations are missing in Gnome. They show up fine in XFCE but not in gnome. 

Anyone has any idea ?

---

### Post by hjlane3 on 2010-10-28
Solution is given in another thread:

[http://ubuntuforums.org/showthread.php?p=9939184](http://ubuntuforums.org/showthread.php?p=9939184)

---

### Post by sylaan on 2010-10-28
I see no solutions in that thread, only workarounds. Which do not work for everyone, me included.

---

### Post by hwttdz on 2010-10-29
So I know some might not want to do this, but I did

cd
mkdir hidden
mv .gconf .gnome2 .gnome2_private/ .gconfd/ .themes/ hidden/

and logged out then back in.  It defaults to the default purple/gray theme, and after changing back to human I picked up the proper color windows.  And these are the packages I have installed that have either gnome or theme in the name

```

adium-theme-ubuntu
dmz-cursor-theme
gnome-about
gnome-applets
gnome-applets-data
gnome-art
gnome-codec-install
gnome-control-center
gnome-desktop-data
gnome-dictionary
gnome-doc-utils
gnome-games-common
gnome-icon-theme
gnome-keyring
gnome-media
gnome-media-common
gnome-menus
gnome-mime-data
gnome-panel
gnome-panel-data
gnome-power-manager
gnome-screenshot
gnome-search-tool
gnome-session
gnome-session-bin
gnome-session-common
gnome-settings-daemon
gnome-splashscreen-manager
gnome-system-log
gnome-system-monitor
gnome-system-tools
gnome-terminal
gnome-terminal-data
gnome-themes
gnome-themes-selected
gnome-themes-ubuntu
gnome-user-guide
gnome-utils
gnome-utils-common
hicolor-icon-theme
human-icon-theme
human-theme
humanity-icon-theme
libgnome-bluetooth8
libgnome-desktop-2-17
libgnome-keyring0
libgnome-media0
libgnome-menu2
libgnome-window-settings1
libgnome2-0
libgnome2-canvas-perl
libgnome2-common
libgnome2-perl
libgnome2-ruby
libgnome2-ruby1.8
libgnome2-vfs-perl
libgnomecanvas2-0
libgnomecanvas2-common
libgnomecanvas2-ruby1.8
libgnomekbd-common
libgnomekbd4
libgnomeui-0
libgnomeui-common
libgnomevfs2-0
libgnomevfs2-common
libgnomevfs2-extra
libpam-gnome-keyring
libsoup-gnome2.4-1
light-themes
network-manager-gnome
network-manager-pptp-gnome
plymouth-theme-ubuntu-text
policykit-1-gnome
python-gnome2
python-gnomeapplet
python-gnomecanvas
tangerine-icon-theme
tango-icon-theme
tango-icon-theme-common

```

This is probably a superset of those needed, but they shouldn't take up much disc space, and it doesn't cause any more processes to run.

---

### Post by chrono_ on 2010-11-01
I'm also experiencing this problem and I've tried all of the proposed solutions and workarounds, but nothing works. Here's what I've found out so far.

I have a machine running Ubuntu 10.10 with FreeNX which I want a few users to be able to remote. They are mostly using Windows (either XP or Windows 7) and have the NX Client installed. The window borders are there when they're remoting, but not visible (i.e. I can press the X button and close a window, etc). However, it only happens during certain circumstances.

When the connectivity type is set to ADSL instead of LAN (or anything higher than ADSL), it works but with poor image quality. This works for me now, but it's not a permanent solution. It also works with any connection type (LAN) when the client uses the same colour depth or lower as the "server" (i.e. 24bpp or 16bpp). 

I've tried from a couple of Ubuntu clients and they all work as they use 24bpp as their colour depth. I've not tried any Mac client so far.

So, I've narrowed it down to this: The borders are missing on Windows clients when using 32bpp colour depth. They create a session with 32bpp on the Ubuntu host (i.e. a session with the geometry 1024x768x32) and this seem to be causing the problem. Is there any way to prevent this?

---

### Post by bo0ork on 2010-11-17
Disable the Render Extension in the NX client software.

Start NX client on your windows machine.
Click "Configure..."
Check the "Use custom settings" checkbox
Click "Settings..."
Check the "Disable the render extension" checkbox
Click Ok
Click Save
Click Ok

Connect as usual.

NOTE: This breaks X applications that (erroneously) rely on this extension, some of which you'll want. Like Synaptic.
Until Canonical and Nomachine decides to play nice with each other, I'd recommend using vnc4server.
Over a local network, it's plenty fast enough and *just works*.

---

### Post by PeteJ on 2011-02-09
Confirming, upgrading NoMachine's nxclient 3.4.0-7 to 3.4.0-10 fixes this problem. 
[http://www.nomachine.com/download-client-windows.php](http://www.nomachine.com/download-client-windows.php)
None of the other solutions worked for me at all.

---

### Post by Zoide7777 on 2011-03-21
> **PeteJ said:**
> Confirming, upgrading NoMachine's nxclient 3.4.0-7 to 3.4.0-10 fixes this problem. 
[http://www.nomachine.com/download-client-windows.php](http://www.nomachine.com/download-client-windows.php)
None of the other solutions worked for me at all.

Thanks so much for the heads-up!  Upgrading the NX client to 3.4.0-10 did the trick for me as well.

---

