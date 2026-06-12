---
title: "GNOME/XFCE Session Overlap?"
date: 2011-08-03
forum: Desktop Environments
---

### Post by rmlrml on 2011-08-03
So, when I check or uncheck a program in the Autostart tab of xfce4-session-settings, it also adds or removes the program in my GNOME Startup Applications (gnome-session-properties), and vice versa.

Why?

This is especially troubling because I would like to be able to have gnome start with the gnome-panel, of course, and xfce NOT start with the gnome-panel, of course.  I am being prevented from doing so.  Now when I start an xfce session at gdm, it starts up with both the xfce panels and the gnome panels over top of each other, crowding each other out.  When I remove gnome-panel from the xfce session, it is automatically removed from the gnome session.

I thought these were separate "desktop environments".  Is that not true?  Are they just inseparable versions of each other, or what?  What's the meaning of this??  :confused:

Is this a result of programmers thinking a person would never want to use more than one desktop environment at different times on the same machine?  At the very least if you're trying to test both DEs you would want to be able to do this, right?

---

### Post by koleoptero on 2011-08-03
There's an option somewhere in xfce session thing, that says "start gnome services on startup". Uncheck that and try again.

---

### Post by rmlrml on 2011-08-03
> **koleoptero said:**
> There's an option somewhere in xfce session thing, that says "start gnome services on startup". Uncheck that and try again.

nope, that setting was already unchecked

---

### Post by nerderello on 2011-10-28
I found that, after installing 11.10 I got the Gnome wallpaper in XFCE, and if I right clicked on this desktop I got the Gnome set of options complete with the Gnome appearance application.

What I had done, in Gnome, was select, in the Gnome Tweak tool (shown as Advanced Settings) in the Desktop 'tab', the slider to turn ON "Have file manager(Nautilus) handle the desktop". I slide this to OFF and now get the XFCE wallpaper and desktop as wanted.

---

### Post by 3Miro on 2011-10-28
nerderello points one solution for the wallpaper in particular. If you want control over the panels and such, you need something else.

What I did was to make startup script that will run on both Gnome and Xfce, however, the script will check which one is running and start only the appropriate services.

```
#!/bin/bash

ISXFCE=`ps -e | grep xfce4-session`

if [ "$ISXFCE" != "" ]; then
#here you can add all XFCE specific applications
gnome-power-manager &
fi

ISGNOME=`ps -e | grep gnome-session`

if [ "$ISGNOME" != "" ]; then
# here you should add the gnome specific apps (i.e. gnome-panel)
/usr/lib/battery-status/battery-status --indicator &
indicator-sysmonitor
fi
```

You can copy paste this into a file in your home/your_name/bin, then give it permissions to run as a program and then add this program to run on both XFCE and Gnome startup. You need to edit it with the appropriate commands, I just wated to use Gnome-poer-manager undr xfce and couple of indicators that would run under Gnome only; you probably want somethinng different.

---

### Post by crdlb on 2011-10-28
Desktop-specific autostart items in /etc/xdg/autostart/ and ~/.config/autostart/ should contain one of:
[LIST]
[*]OnlyShowIn=GNOME;
[*]OnlyShowIn=GNOME;Unity;
[*]OnlyShowIn=XFCE;
[/LIST]

As long as Xfce's GNOME compatibility option is disabled, that should restrict apps to the proper desktop. With that option enabled, however, Xfce will blindly start any autostart item containing OnlyShowIn=GNOME, which is a [direct violation of the autostart spec]("http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html#id2452149").

---

