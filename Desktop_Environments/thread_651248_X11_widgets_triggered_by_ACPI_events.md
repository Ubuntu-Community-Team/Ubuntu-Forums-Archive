---
title: "X11 widgets triggered by ACPI events"
date: 2007-12-27
forum: Desktop Environments
---

### Post by KarT on 2007-12-27
Hi there!

Hi there!

I have a Asus G1 with Gentoo and gnome and after installing acpi4asus i got control over my hotkeys (brightness, volume, wireless, etc). When i increase the brightness, there's a little graphical widget showing up showing me the amount of brightness currently on the lcd. When i decrease, the same happens.

1. In Ubuntu there is also a widget for the volume keys (mute included). How do I enable it?

2. Are there any other widgets (wireless, powermode, etc) similar to those found in Windows? I havent seen any of these in ubuntu..

3. If not, how can i easily develop new ones based on those already made?

It might seem odd that i'm asking here, but i've only seen these in Ubuntu... Thanks for the help :)

---

### Post by vek on 2007-12-27
most of the time, these volume keys tend to be part of the keyboard data.

This means that two steps might have to be involved.

First, gnome (ubuntu) has a configuration panel that defines hotkeys.  inside there, there's keys for volume changing.  You might be able to simply click on those keys there, and reassign them, and then press the volume up/down key to assign that to the function in question.  Basically rebind the keys graphically.

If pressing the volume keys in that configuration tool does nothing (like its not sensing that you're pressing the volume keys), you might need to first tell ubuntu what kind of keyboard you have, or something similar, in the keyboard administration.  So for example changing it from a basic 101 keyboard to a full multimedia keyboard.

As for porting these applications from ubuntu to gentoo, I'm sure that they are specific packages in the ubuntu repositories, and will be normal gnome apps.   The network manager gnome app is very similar to the wireless manager in windows - for me, it shows the signal strength and local wireless networks and lets me choose one, so I think that such a thing does exist, its just a matter of finding its package.  Probably network-manager or gnome-network-manager etc.

I'm also trying to figure out what the widget is that shows up when you alter the volume using the volume keys, so I can hack at that.  If anyone knows, please let me know here too!

---

### Post by KarT on 2007-12-28
I just found out that Gnome has support for those widgets, at least the sound ones.

Now I have a different problem...

I have asus-laptop and asus_acpid daemon installed so that I can configure the triggers for acpi events. When I hit Fn+F11 (volume down), i have a script that calls alsa mixer to decrease the volume of the output. The thing is: If I could create a keyboard shortcut in Gnome for volume down, I'd get the widget I want. The problem is:

- When I hit Fn+[F10,F11,F12], there is a ACPI response as it should, so my DSDT file is fine but...
- When I try to assign the shortcut in Gnome, it doesn't recognize that I'm actually pressing the keys.

Then, I decided to try 'xev' to see the keycodes. Guess what? When I hit those, there's no output. Then, I used 'keycode' [opt] command to see if there was any ouput at all: Nothing.

So I'm guessing.. my tty1 recognizes the keys (it must because it takes actions upon those) but Gnome doesn't. My DSDT is fine (besides the fact that it is working, I followed a guide for my specific laptop), but something really odd is going on here.

Does anyone know what is happening?

PS. When I press volume down key in tty1, the output triggered by asus-laptop module immediately shows up:
```
acpid: received event "hotkey ATKD 00000031 00000030"
```

Concluding:
- DSDT is fine
- Pressing the keys triggers an event, so they're working
- Gnome doesn't recognize the keys
- Neither xev or keycode did output any key when I pressed the while running the programs

Why?

> Most ACPI functions work fine when the kernel module 'asus_acpi' is loaded. LCD-on/off and -brightness (Fn+F7/F5/F6) work out of the box and with KDE a status bar for the brightness level pops up. The other buttons -- all except the WLAN-switch (Fn+F2) -- create ACPI-events which you can read with 'cat /proc/acpi/events', or if the acpi-daemon is running, with 'tail -f /var/log/acpid'.
Now we have to make the ACPI-events trigger an action: install acpid. Inspired by Ubuntu's solution, I think translating ACPI-events to keyboard-events is by far the nicest way for all actions which don't have to run with root privileges. Additionally, if keyboard-events are created, the user can decide what action has to be performed.
I think this answers my questions... thanks!

Thanks!

---

