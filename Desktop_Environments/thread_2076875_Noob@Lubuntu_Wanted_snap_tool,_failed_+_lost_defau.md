---
title: "Noob@Lubuntu: Wanted snap tool, failed + lost default window manager"
date: 2012-10-27
forum: Desktop Environments
---

### Post by DogetiSlaw on 2012-10-27
Hey all, first time poster here, hopefully I judged the forum right and I'm posting this in the appropriate place to solve my problem.

I'm using a fresh install (via Wubi) of Lubuntu 12.1 Me being accustomed to the snap feature in Windows, I ran across this thread below suggesting a way to add basic snap functionality on Lubuntu through a "lightweight compositing manager used by XFCE called xfwm4".

[http://askubuntu.com/questions/73536/is-there-a-lightweight-way-to-snap-windows-in-lubuntu](http://askubuntu.com/questions/73536/is-there-a-lightweight-way-to-snap-windows-in-lubuntu)
(Don't think it's necessary to visit the link for help, but posted it for reference)

The post went on to describe the following to change the default Window Manager to xfwm4:

> To use xfwm4 as your compositing manager instead of OpenBox.
In Desktop Settings - Advanced options change the window manager to xfwm4

Now in terminal:

cd ~/.config/lxsession
mkdir Lubuntu
cp LXDE/* Lubuntu/
Install the compositing manager:

sudo apt-get install xfwm4-themes
Logout and login for the xfwm4 compositing manager to take effect.


I did follow those steps, and successfully changed the window manager to xfwm4. However, I'm not that enthusiastic over the change; I seem to notice some undesirable visual differences, plus I read now that OpenBox has a number of benefits for Lubuntu use over other window managers, and despite all my inexperienced effort I still can't get a great snap tool feature to work.

I'm new to Linux in general, and this is my first time interacting with the Linux community period. I have little to no experience with Linux commands, as I'm a mostly non-technical Windows user. If I'm in the wrong forum (which I would not be surprised about), I'd be more than thrilled to be directed to the right place to learn about changing the Window Manager to OpenBox (or simply the default) so I can use the unique advantages it provides. Plus a snap-tool solution would be helpful.

Any help is very appreciated!

---

### Post by vasa1 on 2012-10-27
Hi! I don't have experience using any Linux via wubi but in case it doesn't make much difference ...

IMO, there was no need of installing xfwm4. You can get what you need from openbox though it may not be as polished as what you get in Windows.  (You use the keyboard, not mouse.) 
Here are a few links to get you started:
[Simple lxde lubuntu aero snap with working obkey keyboard editor]("http://ubuntuforums.org/showthread.php?t=2076433")
and elsewhere:
[[Openbox] Hacks and Configs Thread!]("https://bbs.archlinux.org/viewtopic.php?id=93126")
[Aero Snap in Openbox]("http://crunchbanglinux.org/forums/topic/13968/aero-snap-in-openbox/")

Note that even though the first link mentions installing obkey, it's not necessary at all.

---

### Post by ronniew on 2012-10-27
you might have forgot to do the last part of switching to xfwm4


To use xfwm4 as your compositing manager instead of OpenBox.

In Desktop Settings - Advanced options change the window manager to xfwm4

---

