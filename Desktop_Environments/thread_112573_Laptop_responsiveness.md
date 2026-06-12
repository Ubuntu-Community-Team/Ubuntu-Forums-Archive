---
title: "Laptop responsiveness"
date: 2006-01-04
forum: Desktop Environments
---

### Post by Skye on 2006-01-04
Hey folks!

I just bought a new compaq laptop (v2402us) which is now running Ubuntu Breezy. System specs are as follows:

AMD Sempron M 2800+ processor
256 MB ram
4,200 rpm HDD
ATI m200 graphics card
ATI IXP chipset

When I try to load programs, and especially when updating through apt-get or synaptic (it doesn't matter which one I use) my CPU usage spikes with what the gnome panel system monitor identifies as *IOWait*, and not *User* or *System*.  What is IOWait? Can I make that specific part of my system (whatever it is) faster?

It's certainly not unbearable by any means, but I was wondering if there was anything I could to increase general system responsiveness, short of buying more ram- that's something I plan to do eventually, but I don't want to spend the money on ram right now.

What I have done so far is this:
-Installed a k7 kernel (from repos, not custom)
-Made sure DMA was enabled on my HDD
-Switched to xfwm from metacity for a window manager- still running gnome, though
-Installed the ATi flgrx drivers (the default ATi drivers crashed when I tried to log out from an x sesson)
-Gotten rid of extraenous processes using the Ubuntu BootUp Manager and the Services applications.

I don't need 3d acceleration on this machine, seeing as I don't play games or expect to use any fancy graphics effects, but since the default "ati" x drivers crash, I figured I had to use the fglrx drivers- am I wrong?

Any help anyone could provide would be much appreciated.  Thanks!

---

### Post by cwmccabe on 2006-01-04
I can't answer your question, but to help the thread along (because I have the same problem), here are links to other threads concerning a similar problem.  In most these threads this problem is also unsolved, but I wonder if they will help somebody put the pieces together to find out what the problem is.

Slow memory IO can anyone figure out why?
[http://ubuntuforums.org/showthread.php?t=102489&highlight=iowait](http://ubuntuforums.org/showthread.php?t=102489&highlight=iowait)

Disk I/O taking exhorbitant CPU 
[http://ubuntuforums.org/showthread.php?t=99988](http://ubuntuforums.org/showthread.php?t=99988)

high iowait
[http://ubuntuforums.org/showthread.php?t=99572](http://ubuntuforums.org/showthread.php?t=99572)

constant iowait cpu usage
[http://ubuntuforums.org/showthread.php?t=81582](http://ubuntuforums.org/showthread.php?t=81582)

System has 10% + iowait
[http://ubuntuforums.org/showthread.php?t=51744](http://ubuntuforums.org/showthread.php?t=51744)


You might also look at this one, the double-clock speed problem.  (It wasn't it for me). [http://ubuntuforums.org/showthread.php?t=53094](http://ubuntuforums.org/showthread.php?t=53094)

---

### Post by Skye on 2006-01-04
Hrm... this problem with IOwait seems to be pretty widespread, assuming that it is in fact a problem and not a result of slow hardware- have any bug reports been filed?

Does anyone else have any suggestions for general system responsiveness?

---

