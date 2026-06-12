---
title: "gnome / kde taskbar weirdness"
date: 2006-11-06
forum: Desktop Environments
---

### Post by sedd on 2006-11-06
I'm using gnome for my desktop environment, but I use a lot of kde apps, mostly kate and kdevelop. When I change virtual desktops / workspaces ( you know, ctrl-alt-left or right ) the kde apps send the "need attention" signal to the window manager, like in gaim when someone sends you a message. The taskbar item for that app starts glowing and pulsing. It happens if the kde app is not focused when I switch to its desktop. 

To see if this happens to you, open two kwrite windows (or konsole or whatever. just open two) and hit ctrl-alt-right to switch workspaces then hit ctrl-alt-left to switch back. (Or use the pager applet.)   Does one of the kde apps have a flashing taskbar thingy? Is this just me?

I would post a bug report to either the gnome or kde lists, but I don't know who's responsible. It may be nobody's fault because gnome and kde use different protocols for the taskbar flashy signal. I hope not.

---

### Post by benp on 2006-11-15
Have you made any progress with this? I have exactly this problem, running Edgy dist-upgraded from Dapper. I can't remember whether it happened in Dapper.

I've tried disabling taskbar notifications for every KDE app via kcontrol, but that didn't help.

I would be completely content to entirely disable taskbar flashing, but that doesn't seem to be an option for some reason.

---

### Post by Joe Momma on 2007-05-01
I'm seeing the same problem too.  If konsole is not in focus and I change desktops and go back, the button in the taskbar pops up and pulses at me and continues pulsing even when I switch to a different desktop.

anybody have any ideas how to stop this?

I'm using feisty with gnome, and I don't remember seeing it in edgy.

---

### Post by Joe Momma on 2007-05-15
anybody?

This is really bugging me because I have a konsole open on each desktop and as I work, eventually I end up with 5 different konsole taskbar items pulsing at me.  It makes it hard to tell which one I actually want to click on, and I have to click through them all if I want to shut them up

---

### Post by jocker on 2007-08-13
Exact same thing happening here (with Feisty fresh-installed).

Any luck anyone with this??? :confused:
I've tried disabling each and every option that mentions blinking/flashing tray, in both gnome & KDE preferences, but to no avail...

HELP, it's getting on my nerves! I hate to drop using Konsole, just because the taskbar misbehaves... It's really ridiculous, I know, but it's a great annoyance...](*,)](*,)](*,)

ANY help appreciated...

Thnx...
   Jocker

---

### Post by rafaelcpr on 2007-08-15
It also happens to me...konsole and kate blink back at me wherever i go.

---

### Post by findarunhere on 2007-08-21
Any workaround for this???

---

### Post by jocker on 2007-09-11
> **findarunhere said:**
> Any workaround for this???

Personaly, I switched from gnome to XFCE where this problem doesn't occur. But this is still not a viable solution IMHO...
:frown:

---

### Post by jocker on 2007-10-01
OK, I've had it! Back to Gnome for me (XFCE is too crash-prawn on my system). :(
and to get rid of this annoyance? Out goes Konsole, in comes "multi-gnome-terminal".

It has a very similar feature-set as Konsole, perhaps a bit less user-friendly, but no task-bar blinking, so to my eyes, it is a winner! :KS

Good luck to all of you out there with other KDE-based apps. I for once have found my medicine. :)



Thnx...
    Jocker

---

