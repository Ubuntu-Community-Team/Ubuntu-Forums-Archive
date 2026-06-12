---
title: "Desktop won't start"
date: 2007-02-03
forum: Desktop Environments
---

### Post by tim_astley on 2007-02-03
Folks,
I am having a frustrating time trying to get Ubuntu to work on my 'old' PC.
I have installed it and it all works fine in the good old fashioned 'command line' world.
I wanted to get the desktop working - I thought I had installed all I needed when I originally installed it ages ago - but on running 'startx' the monitor just went blank and that was that.

So I installed ubuntu-desktop
and started gdm
and I got the same result. The screen flashes and then the monitor puts itself into standgy mode. I can get back to the command line by using ctrl-alt-F1 (I learnt something new today).

I have looked at the logs and searched various forums but nothing seems to be awry.  I have seen a number of things that could be the cause.
**1. Fonts? ** 
I was getting errors about various fonts not being found and I edited the XF86Config-4 file to stop it loading thr FontPath  "unix/:7100" 
that got rid of the error messages but nothing else.

**2. Permissions?**
I also note that I get authentication failures.  When the screen goes blank I hit the space bar a few times to see if it needed some 'prompting' and in auth.log I see lines like
localhost gdm[5564]: (pam_unix) bad username [  ]
and above that
localhost gdm[5564]: (pam_unix) check pass; user unknown

Makes me wonder if somewhere I have to tell gdm about who can log on and who can't?

**3. Video capability/memory?**
There are also quite a few lines in XFree86.0.log along the lines of
Not using mode "blahxblah@blah" (insufficient memory for mode)
or (bad mode clock/interlace/doublescan)
but it does seem to get down to some default modes later on which it seems happy with.

I am hopeful there is a simple fix for this.

I appreciate any help

Cheers
Tim

---

### Post by taurus on 2007-02-03
```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by tim_astley on 2007-02-03
> **taurus said:**
> ```
sudo dpkg-reconfigure xserver-xorg
startx
```

Herein lies a problem.
Package `xserver-xorg' is not installed and no info is available.

I installed 'ubuntu-desktop' - so why isn't this there already?

Should I install xserver-xorg or will I cause further problems?

Tim

---

### Post by gradedcheese on 2007-02-04
ubuntu-desktop is a meta-package that actually has little to do with X.  You should indeed install xserver-xorg which is the actual X server, then 'startx' and see what happens.  If you're having trouble after that, you can look at the xorg log, they're named like this:

/var/log/Xorg.0.log

---

### Post by tim_astley on 2007-02-04
Thanks guys.
Still got a problem
When I run
sudo apt-get install xserver-xorg
I get
E: Couldn't find package xerver-xorg

I have edited /etc/apt/sources.list to ensure I check the universe for packages but that made no difference (and I guess it shouldn't).

So, my next question is - how do I install xserver-xorg or was it called something else in the past?

Cheers
Tim

---

### Post by gradedcheese on 2007-02-04
hmm... which version of ubuntu are you using?  perhaps it's a much older release that still used xfree86?

---

### Post by tim_astley on 2007-02-04
Warty Warthog - 4.10

Once I get this working - I'll be asking how to upgrade :) 

Thanks
Tim

---

### Post by gradedcheese on 2007-02-04
oh!  That's the very old first ubuntu release (and no longer officially supported), after which they dumped xfree86 (good riddance) in favor of xorg.  Well, I haven't used that one in a long time, but...

```
sudo dpkg-reconfigure xserver-xfree86
```

should do it?  If not:

```
sudo xdebconfigurator
```

---

