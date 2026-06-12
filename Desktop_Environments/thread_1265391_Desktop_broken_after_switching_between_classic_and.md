---
title: "Desktop broken after switching between classic and netbook"
date: 2009-09-13
forum: Desktop Environments
---

### Post by pink_book7 on 2009-09-13
Hi
I'm a linux newbie, so please be gentle with me!

I changed the desktop display on my Acer Aspire from Classic to Netbook, but something went wrong.  Now the background looks like the original classic and the line across the top looks like the Netbook desktop.  I have no menus, right clicking on the desktop does nothing.  Alt-F1 brings up the applications menu.  I can run terminal, firefox etc ok, but the desktop doesn't update properly so after a while I end up with 'frozen' versions of the apps menu everywhere.  Rebooting achieves no improvement.

Can anyone help, please?  Thanks. :confused:

---

### Post by j0vial on 2009-09-13
Set from Preferences -> Appearance -> Visual Effects to None


and try installing this updated version of desktop switcher [http://launchpadlibrarian.net/26020903/desktop-switcher_0.4.6_i386.deb](http://launchpadlibrarian.net/26020903/desktop-switcher_0.4.6_i386.deb)

and follow instructions from here: [https://bugs.launchpad.net/desktop-switcher/+bug/349519?comments=all](https://bugs.launchpad.net/desktop-switcher/+bug/349519?comments=all)

---

### Post by pink_book7 on 2009-10-04
Hi

Apologies for the delay in replying I've been away with work.

I've tried the fix suggested by installing the deb, but I still can't switch between classic and netbook desktops.  Classic works fine now, but the netbook desktop is always broken no matter what I do.  There are a number of errors that appear in terminal when I try to switch to it, see below, hopefully they'll make sense to someone!

Any help would be gratefully received.

Thanks

```
claire@claire-laptop:~$ desktop-switcher
In classic mode: true
** (desktop-switcher:4628): DEBUG: Enabling netbook mode
** (desktop-switcher:4628): DEBUG: Enabling launcher autostart
** (desktop-switcher:4628): DEBUG: Launching the, er, Launcher
unhandled buffer attach event, attacment type 7
unhandled buffer attach event, attacment type 7
** (desktop-switcher:4628): DEBUG: Restoring panel settings

** (netbook-launcher:4634): WARNING **: Failed to send buffer

** (netbook-launcher:4634): WARNING **: Failed to send buffer
** (netbook-launcher:4634): DEBUG: CONFIG: Low graphics mode: False
** (netbook-launcher:4634): DEBUG: CONFIG: Font dpi: 96.000000
** (netbook-launcher:4634): DEBUG: CONFIG: Font changed: Sans 10

** (netbook-launcher:4634): DEBUG: CONFIG: Connecting to ConsoleKit for suspend/resume restarting
** (desktop-switcher:4628): DEBUG: 
Restored panel configuration from: /home/claire/.config/desktop-switcher/netbook-panel-config.xml

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2600003 (Switch Des)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
** (desktop-switcher:4628): DEBUG: Removing nautilus from gnome session startup

** (desktop-switcher:4628): WARNING **: Failed to send buffer

** (desktop-switcher:4628): WARNING **: Failed to send buffer
claire@claire-laptop:~$ Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1800434 (.config - )
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2a00003 (claire@cla)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
claire@claire-laptop:~$ Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1800434 (.config - )
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
** (netbook-launcher:4634): DEBUG: PLACES: Volume Added: 43.0 GB Media /org/freedesktop/Hal/devices/volume_uuid_60840A7C840A54C6
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2a00003 (claire@cla)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
unhandled buffer attach event, attacment type 7
unhandled buffer attach event, attacment type 7

```

---

