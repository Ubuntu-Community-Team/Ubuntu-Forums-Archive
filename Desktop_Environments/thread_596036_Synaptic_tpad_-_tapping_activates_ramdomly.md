---
title: "Synaptic tpad - tapping activates ramdomly"
date: 2007-10-29
forum: Desktop Environments
---

### Post by 4nick8or on 2007-10-29
Hello : 
    This has me stumped-
         I have three desktops installed, Gnome, KDE, and X (installed in that order). Plus the icewm. Running 7.10 Ubuntu. 

When I start an X session the background goes to black with one icon set, and after a bit loads my gnome background and icons. I've set the desktop to use X to control the session, but that only holds for a short while.(?) Importantly to me, is that I have tapping off on the touchpad in gnome, but when the X desktop reverts to the gnome style, it's on, and it's touchy!
 
     Also, if I'm running Ubuntu Gnome (my default), sometimes the tapping is activated for no apparent reason. And when that happens the tpad is super touchy. I cannot relate it to a specific program, seems random, but happens more if I run a file manager - Nautilus or Thunar..... any forum members seen this behavior? I'm on the verge of removing the other desktops and window managers, but I have much fun comparing them. 
 
  Have I found a bug in 7.10, or have I introduced one?

Regards, Tom

---

### Post by kerry_s on 2007-10-29
that sounds like something you did, screwed up the way the desk top works.
you can disable tapping in xorg.conf.

gksudo gedit /etc/X11/xorg.conf

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "MaxTapTime" "0"
EndSection


```

---

### Post by Zorael on 2007-10-29
And you can install gsynaptics/ksynaptics. You'll need to add
```
Option "SHMConfig" "on"
```
to the touchpad xorg.conf section to get it working, though.

You can disable tapping in there, as well as change sensitivity, pad borders (for scrolling), amongst other stuff.

---

### Post by 4nick8or on 2007-10-30
OK. Thanks for the replies. I 've restored stability by editing the xorg. conf settings. Effectively solved, but still unsolved is why it happened in the first place... I thank the responders for the practical solution. But I will wonder what screwed the pooch, so it can be avoided in the future.

---

### Post by Toby Bartels on 2008-02-13
I also have this problem, and I didn't do anything funny like installing multiple desktops.

I'm using a Dell Inspiron E1505, bought from Dell with Feisty preinstalled. I turned on SHMConfig (in xorg.conf), installed synaptic, and then then configured the touchpad entirely through the GUI. I turned off tapping; I've always hated that. And all was well.

Then I upgraded to Gutsy, and now tapping will turn on --randomly as far as I can tell-- a couple of times every week. It does this separately for each user (there are three, all with tapping turned off.) So then I go to System -> Preferences -> Touchpad and turn it off again.

I will try setting MaxTapTime in xorg.conf as kerry_s suggested, then report back in a couple of weeks if all goes well. (Since it's random and rare, I can't test it more quickly than that --unless it fails, of course.)

---

### Post by Toby Bartels on 2008-02-13
> **me said:**
> I will try setting MaxTapTime in xorg.conf as kerry_s suggested, then report back in a couple of weeks if all goes well. (Since it's random and rare, I can't test it more quickly than that --unless it fails, of course.)

Well, I can at least confirm that, having done this and restarted X, I can no longer use tapping even if I turn it on --not an ideal solution, but what I expected to happen. And then if I restore xorg.conf to its previous state and restart X, then I *still* can't use tapping even if I turn it on --that can't be right!

Well, I don't really understand what the deal is, but at least it will work for my users, since none of us (really neither of us, the third exists only to perform system administration) happen to want tapping.

---

