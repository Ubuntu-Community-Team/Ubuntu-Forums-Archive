---
title: "Fluxbox and Openbox crash when mounting USB device."
date: 2008-07-15
forum: Desktop Environments
---

### Post by DocYoung on 2008-07-15
I've noticed both flubox and openbox crash when mounting a USB device. It seems to bring up gdm with ubuntu's default background. This leaves no menu's as left mouse click brings up nothing and right mouse click bring up gnomes stuff. 

Any ideas? 

Did I do something wrong with installation of fluxbox or openbox?

---

### Post by urukrama on 2008-07-15
What do you use to mount the USB drive? Do you have a volume manager running? 

Did you install Openbox and Fluxbox on a regular Ubuntu install, or on a command-line install?

---

### Post by RedSquirrel on 2008-07-15
That sounds like nautilus taking over the desktop. Be sure to run it with the "--no-desktop" option when you run it in Openbox or Fluxbox:

```
nautilus --no-desktop
```

---

### Post by snowpine on 2008-07-15
Hi Doc, it sounds like you are trying to use Nautilus, is this correct? To run Nautilus in Fluxbox, use 'nautilus --no-desktop' instead of just 'nautilus' and that should stop the Gnome desktop from loading. Give it a try!

(edit) Red Squirrel, you are too fast for me!!!

---

### Post by DocYoung on 2008-07-15
Anyway to stop the auto mount feature?


... and thank you for you help.

---

### Post by DocYoung on 2008-07-15
> **urukrama said:**
> What do you use to mount the USB drive? Do you have a volume manager running? 

Did you install Openbox and Fluxbox on a regular Ubuntu install, or on a command-line install?

Default ubuntu (8.04) with aptitude install for both Openbox and Fluxbox.

---

### Post by RedSquirrel on 2008-07-15
> **DocYoung said:**
> Anyway to stop the auto mount feature?

Are you starting any Gnome programs (for example, for volume management) in your ~/.fluxbox/startup? You could turn them off (comment them out -- put a '#' in front).

The same goes for your ~/.config/openbox/autostart.sh file. If you don't have that file, you could copy the default from /etc/xdg/openbox and comment out the stuff that relates to GNOME in the local autostart.sh file (that is, ~/.config/openbox/autostart.sh).

I haven't used GNOME for over a year and half, so perhaps urukrama or someone else will have a better suggestion for stopping its auto mounting.

---

### Post by DocYoung on 2008-07-16
Fluxbox startup

```
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
# fbsetbg -f /home/odin/pictures/wallpaper.png
#
# This sets a black background

/usr/bin/fbsetroot -solid black

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp "/home/odin/.fonts"
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap "/home/odin/.Xmodmap"



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &
nm-applet &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
exec /usr/bin/fluxbox -log "/home/odin/.fluxbox/log"
```

Openbox startup
(cp from /etc/X11/*/ to /home/odin/*/autostart.sh)

```
# This shell script is run before Openbox launches.
# Environment variables set here are passed to the Openbox session.

# Set a background color
BG=""
if which hsetroot >/dev/null; then
    BG=hsetroot
else
    if which esetroot >/dev/null; then
	BG=esetroot
    else
	if which xsetroot >/dev/null; then
	    BG=xsetroot
	fi
    fi
fi
test -z $BG || $BG -solid "#303030"

# D-bus
if which dbus-launch >/dev/null && test -z "$DBUS_SESSION_BUS_ADDRESS"; then
       eval `dbus-launch --sh-syntax --exit-with-session`
fi

# Make GTK apps look and behave how they were set up in the gnome config tools
if which gnome-settings-daemon >/dev/null; then
  gnome-settings-daemon &
fi

# Preload stuff for KDE apps
if which start_kdeinit >/dev/null; then
  LD_BIND_NOW=true start_kdeinit --new-startup +kcminit_startup &
fi
```

This is what I should # out?

# Make GTK apps look and behave how they were set up in the gnome config tools
if which gnome-settings-daemon >/dev/null; then
  gnome-settings-daemon &
fi

It seems to be the only thing gnome related in the two files. 

I've been researching and it doesn't look like I should completely remove nautilus as is has a hand in alot of other roles.

---

### Post by DocYoung on 2008-07-16
I got a sudo fix for this problem. in the fluxbox menu I've changed the default line to start nautilus to the {nautilus --no-desktop}.

it still auto mounts but it doesnt pop open like plug and play. I've tried 2 memory sticks, 1 ipod, 1 backup hard drive (80g). It would seem that the mem sticks need to be force mounted.

One fix seems to make another problem. What better to learn linux!!

---

### Post by urukrama on 2008-07-16
> **DocYoung said:**
> I've been researching and it doesn't look like I should completely remove nautilus as is has a hand in alot of other roles.

You could not use Nautilus in Openbox and Fluxbox (without the need to remove it from your system), and use a different file manager like Thunar. If you install Thunar's volume manager plugin ([thunar-volman]("http://packages.ubuntu.com/hardy/thunar-volman")) as well, Thunar will automount your flash drives, CDs, etc. As Thunar is a lot lighter than Nautilus, this might give you a smoother Open/Fluxbox experience as well.

If you want to do so, just remove all your Nautilus entries from your menus, and replace them with entries for Thunar.

Your fluxbox autostart file does not contain any Gnome components. Gnome-settings-daemon in your Openbox sessions controls your Gtk theme, icons theme, fonts, etc. You could remove that and set the Gtk theme in a different way (see [here]("http://urukrama.wordpress.com/openbox-guide/#Gtkthemes") for more info). It doesn't control your disks, etc. [Gnome-volume-manager]("http://packages.ubuntu.com/hardy/gnome-volume-manager"), which you don't have in your autostart file, does that, but it seems once Nautilus is running it also can mount disks without gnome-volume-manager.

You can easily modify your autostart file for your needs (See [here]("http://urukrama.wordpress.com/openbox-guide/#Autostart") for help on how to do so in Openbox). If you decide to use Thunar, add the following line to your autostart file to automount drives before you open a Thunar window:

```
thunar --daemon &
```

I'm not exactly sure what you want to happen when you insert your memory stick, though. Do you want the disks to automount and "pop up like plug and play"?

If so, if you use Thunar and thunar-volman, you can specify that: go to Edit > Preferences > Advanced and click on "Configure" (under "Volume management"). You can then easily tell Thunar what exactly you want to happen when you insert removable media, such as memory sticks.

In Nautilus, you can change those settings in Edit > Preferences > Media. To disable Nautilus from opening a new window, untick the box before "Browse media when inserted" (at the bottom of the window). I just tested this (I normally don't use Nautilus in Openbox), and it does mount my memory stick, but doesn't open a new window for it.

I hope this helps.

---

### Post by DocYoung on 2008-07-16
[B]> **urukrama said:**
> 
In Nautilus, you can change those settings in Edit > Preferences > Media. To disable Nautilus from opening a new window, untick the box before "Browse media when inserted" (at the bottom of the window). I just tested this (I normally don't use Nautilus in Openbox), and it does mount my memory stick, but doesn't open a new window for it.


This and ...

```
nautilus --no-desktop
```

... changed in fluxbox's menu seems to have fixed the problem. It hasn't crashed after these changes.

Thank you all for your advice its been spot on!

---

### Post by urukrama on 2008-07-17
> **DocYoung said:**
> It hasn't crashed after these changes.

As far as I could tell from what you wrote, Openbox or Fluxbox did not crash, but Nautilus just took over. When Nautilus controls the desktop (icons and wallpaper), Fluxbox and Openbox cannot use it for the right click menu. They would still run, but are overpowered by Nautilus.

But I'm glad it is solved!

---

