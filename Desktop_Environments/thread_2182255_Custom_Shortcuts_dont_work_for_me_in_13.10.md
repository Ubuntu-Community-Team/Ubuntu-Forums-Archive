---
title: "Custom Shortcuts dont work for me in 13.10"
date: 2013-10-20
forum: Desktop Environments
---

### Post by mcpish on 2013-10-20
Weird problem.  I upgraded to Ubuntu 13.10 and I can't seem to set any working "Custom Shortcuts".

In the Keyboard settings I go to the Shortcuts tab like I always have and try to create some new "Custom Shortcuts".
I want to set Nautilus to open to a particular network drive I have mounted when I press one of the 5 launch keys on my keyboard.

So I have the command as "nautilus /media/HD2" and set it to Launcher5 key which it properly detects when I press it to set which key it should be, but it doesn't end up doing anything.

I've had it set this way before in previous versions of Ubuntu.  All the built-in keyboard shortcuts work but I just can't create new "Custom Shortcuts".   

I've tried everything, tried setting a new shortcut for <CONTROL> + <ALT> + <C> and again nothing.  It lets me set it, but the combination ends up doing nothing.

---

### Post by mcpish on 2013-10-20
I just solved my own problem.

After setting custom shortcuts, you have to logout of Ubuntu and Log back in, then they work.  That wasn't the case in previous versions; they used to just work right away.

---

### Post by mc4man on 2013-10-20
> **mcpish said:**
> I just solved my own problem.

After setting custom shortcuts, you have to logout of Ubuntu and Log back in, then they work.  That wasn't the case in previous versions; they used to just work right away.
Correct, there was an issue right before release that if gnome-screensaver wasn't installed then custom shortcuts would never work.
That was fixed but as seen you have to log out/in when setting new ones.
(seems like a bug, gnome-settings-daemon continues to present issues in Ubuntu

---

### Post by mcpish on 2013-10-20
Thanks for the heads-up

It's always a bit of an excercize in frustration when new versions of Ubuntu come out.  They loving adding features.. ..but never fixing bugs.  And even if they fix a bug, they end up adding a new feature which creates 3 new bugs or break things that were working before, but aren't now.

It's been the same excersize every six months for the past 4-5 years for me.  Install Ubuntu, then spend the next day or so reapplying every little fix and workaround to get the OS working like a proper desktop OS.

Such as, installing CCSM to:
  get rid of the annoying Window Snapping,
  Turn off the buggy "Detect Refresh Rate" checkbox in the Composite section

Creating a new startup command to autofix the choppy window dragging behavior by forcing the compiz refresh rate to 180 at startup:
[B](sh -c "sleep 10 && dconf write /org/compiz/profiles/unity/plugins/composite/refresh-rate "180" &")

[/B]Turning off the annoying Global Menus (This isn't a 9" Mac from 1984) 

Turn off the buggy focus stealing prevention 

Reduce the size of the Unity sidebar icons to something reasonable (38)

Setting up dual monitors correctly (Ubuntu always swaps the order of the monitors by default), get rid of that annoying edge mouse stickyness that's on by default, and the iconbar should ONLY show up on one of the monitors by default.

Changing the default sound output device to "digital SPDIF" not "analog" (this should be autodetected based on what's plugged in)

I think Canonical really needs to work on that stuff first before adding **ANY** new features.  It takes a good 4-6 hours after installing EVERY new release of Ubuntu and it's always exactly the same issues no matter what computer I install it on.

Forget about this "ubuntu cloud nonsense" and "amazon searching" which nobody cares about and work on the long standing bugs.

I just don't understand Canonical's priorities.

---

### Post by emailme-t on 2013-11-14
How do you make SPDIF the default connection?  That's been driving me nuts for a year now.

---

### Post by stallinux on 2014-01-14
Indeed!! And, what is worse, with the new versions we are now asked to donate money, which is all very well, but then the options for application of the money does NOT INCLUDE "fixing bugs". I do not care about new features (Ubuntu Cloud is crappy compared to Dropbox. Unity is crappy; my computer is not a telephone, duh! Who wants to snap windows!! Etc.), but the old features were PERFECT. Now there is a persistent bug that my user-defined keyboard shortcuts do not work. And, by the way, also the embedded shortcuts (like keyboard switcher) fail. Now we are slowly drifting towards a nice 'snappy' OS that is useless.

Now, **does anybody know how to make keyboard shortcuts work** again? Simple log-off/logon/reboot does not work. (13.10 32 bit). Other buggy feature is the HP printer driver. It asks me EVERYDAY to re-install all the (50?) printers on our network. But that is HP's doing I guess.

---

### Post by Ducktor on 2014-01-21
I also have the issue. I set up my shortcuts ages ago, so obviously a logout/login would not work. I had earlier a bug, which was the opposite: after logout/login the shortcuts had to be set again. Now neither workaround works. After login, the shortcuts cannot be used, and after re-setting them, still they're broken. What pisses me off these times is my own fault actually, that I don't know how to find out the problem, I don't know how to start debugging this issue. Can anyone help?

---

### Post by frank-breitling on 2014-07-17
Same problem here. And logout / login doesn't fix it.

---

### Post by coffeecat on 2014-07-17
13.10 reached end of life today, so there is no point in any further necromancy of this old thread.

If anyone is reading this thread and is still running this now unsupported version of Ubuntu, please upgrade to or re-install with a currently supported version. If anyone needs help with any issues described here, then please start a new thread, but only if you are running a supported version of Ubuntu. If you are running 13.10, the advice will be the same: upgrade or re-install.

Thread closed.

---

