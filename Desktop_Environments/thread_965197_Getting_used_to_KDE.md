---
title: "Getting used to KDE"
date: 2008-10-31
forum: Desktop Environments
---

### Post by gamelord12 on 2008-10-31
I just switched from Ubuntu 8.04 to 64-bit Kubuntu 8.10.  I'm trying to find a few things that even after a few hours of tinkering, I couldn't figure them out.

How do I adjust my mouse trackpad, namely so that tapping the trackpad DOES NOT click?

How do I change the logo on the menu to the Ubuntu or Kubuntu logo rather than the KDE logo?

When I tried turning on the graphical effects built-in to KDE, my screen went black except for my mouse.  Every time I tried logging in after that, my screen stayed black.  I tried repairing X from the recovery console, and it did nothing.  I ended up re-installing.  I want to try out these graphical effects without it ruining my system.  How can I make sure I don't get stuck in this mess again?  I'm using a GeForce 8400M in a Dell 1420n laptop by the way.

---

### Post by Kalinda on 2008-10-31
First of all, as you're using Kubuntu Intrepid, this means you're using KDE 4, which is still new and quite buggy. I actually find the desktop effects work better than the Compiz ones, as they don't cause problems with video playback, but they are still bugtastic.

You might be better off sticking to Gnome or following [this thread]("http://ubuntuforums.org/showthread.php?t=963695") to use KDE3 with Intrepid, as it's much more stable. I dunno how well that HowTo works, though. I'm still using Hardy.

I'll try to help you anyway.

> **gamelord12 said:**
> How do I adjust my mouse trackpad, namely so that tapping the trackpad DOES NOT click?
Go into System Settings, go to keyboard and mouse, click on mouse, then click the "double click to open files and folders" checkbox. This is also the same in KDE3.

> How do I change the logo on the menu to the Ubuntu or Kubuntu logo rather than the KDE logo?
You mean the KMenu logo? That is determined by your icon theme. However, if you get a standalone KMenu icon from, say, kde-look.org then you'll have to replace the default Oxygen one with your new one.

In order to do this, you'll have to figure out which folder KDE4 keeps its default Oxygen icons in, since I honestly have no idea. The file name should still be 'kmenu.png', though. So just do a search for it.

> When I tried turning on the graphical effects built-in to KDE, my screen went black except for my mouse.  Every time I tried logging in after that, my screen stayed black.  I tried repairing X from the recovery console, and it did nothing.  I ended up re-installing.  I want to try out these graphical effects without it ruining my system.  How can I make sure I don't get stuck in this mess again?  I'm using a GeForce 8400M in a Dell 1420n laptop by the way.
Can't be much help here, I'm afraid. It sounds like a bug. I'd suggest using the official Nvidia drivers, but you probably already are so I don't know.

Like I said, you might just be better off using Gnome until KDE4 gets its house in order. Hopefully that'll happen in version 4.2

---

### Post by gamelord12 on 2008-10-31
Okay, I started using Compiz instead of KDE effects (as it turns out, I THOUGHT I had enabled nVidia drivers last time, but I hadn't), and I like Compiz's amount of features better, but I can't figure out how to get four workspaces.  For some reason, when I use Compiz, it keeps me stuck at two instead of four workspaces.  How do I fix this?

---

### Post by gamelord12 on 2008-11-01
*Go into System Settings, go to keyboard and mouse, click on mouse, then click the "double click to open files and folders" checkbox. This is also the same in KDE3.*

That doesn't fix my problem, it just makes it slightly less annoying.  I don't want my trackpad to click at all.  I have buttons for that.  How do I do this?

---

### Post by gamelord12 on 2008-11-04
Anyone know how to fix the trackpad thing?  Also, before I re-installed my OS, I think Compiz clashed with KDE and caused it to boot without X sometimes.  Any way to make them play nice?

---

### Post by benerivo on 2008-11-04
I think you can disable the touchpad click feature using [this guide]("http://strabes.wordpress.com/2006/11/04/turn-off-annoying-touchpad-tap-click-in-ubuntu/").
I don't know about the compiz feature in kubuntu, but compiz tends to integrate better with gnome than kde. How are you starting compiz? During login, or manually after kde has begun?

---

### Post by Urzumph on 2008-11-04
I had the screen-goes-black issue as well.

As I recall I fixed it by going to ~/.kde/shared/settings/kwinrc

and disabling compositing. Then restart your X.

(That path may be wrong, that was off the top of my head).

---

### Post by OffAxis on 2008-11-05
Regarding the touchpad, I think you can still edit the /etc/X11/xorg.conf and have it turn the tapping on/off.
Look for the "MaxTapTime" option and set it to zero.

```
Option      "MaxTapTime"            "0"    # 0 disables tap-to-click, set it to 100 to re-enable
```

Then restart your x-server.

---

### Post by gamelord12 on 2008-11-05
Why isn't there a GUI tool for this yet?  GNOME's got one.  I just can't get a perfect mesh of the things that I like in each desktop environment.

---

### Post by gamelord12 on 2008-11-06
My xorg.conf file doesn't have a section for input devices...

---

### Post by der_Dieb on 2008-11-23
Here's the solution I used for my trackpad issue.  This is on a Dell Inspiron 1420 with a Synaptics trackpad.  

In KDE 4, the configurations for the trackpad was disabled from the xorg.conf file (That's why it either doesn't appear there anymore or is commented out).  The setup is done in HAL now, which must be configured.

You'll have to create a new configuration file for HAL to read.  The file to create is "/etc/hal/fdi/policy/11-synaptics-options.fdi".    

Here is the exact code to enter into the file "11-synaptics-options.fdi":

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" contains="synaptics">
    <merge key="input.x11_options.MaxTapTime" type="string">0</merge>
  </match>
</device>
</deviceinfo>

```

After the new file has been created, restart the machine.

---

