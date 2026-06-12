---
title: "Weird freezing problem on Dell Mini 9"
date: 2010-01-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by NionBohart on 2010-01-19
I'm having a strange freezing problem on my Dell Mini 9 and it's just about got me completely vexed.

Here's the problem: my Dell Mini 9 regularly freezes. By regularly, I mean every day. And by freezing, I mean a complete system lockup (screen frozen, no network login possible, SysRq magic keys don't work).  The only thing I can do when it freezes is hold the power key down until it switches off.

Now here's the weirdness: once it's frozen and I've been forced to switch it off and on again, it will run for the rest of the day with no problems. When it's frozen once, it won't freeze on the next boot - no matter how long I leave it running.  It's not simply that it freezes on every other boot. I tried working around the problem by double booting, but it still freezes. 

Currently I have Karmic UNR on it, but it's the same with the original Dell 8.04 Ubuntu, Dell 9.04 Ubuntu, and regular versions of Intrepid and Jaunty (including Jaunty UNR).  I even tried Fedora 12 and it's just the same. I don't have Windows to try that.

No application causes it. It's frozen with firefox on the screen, in the middle of opening a terminal, with the screensaver running and with no applications running.

I thought it might be a hardware problem or overheating (with no fans, the mini 9 runs hot). But what kind of hardware problem is 'fixed' by a lockup, and it runs just as hot on the second 'good' boot as the first.

There's nothing helpful in /var/log/messages or dmesg. Leaving 'top' running to see what it's doing when it freezes doesn't reveal any pattern.

I guess I should send it back, but I'm reluctant to as it's a nice little machine otherwise.  

Anyone have any ideas? Any debugging/problem solving tips to isolate the piece of HW/SW causing this?

---

### Post by kakotako on 2010-01-21
I have a similar problem on mine with 8.04 that came preinstalled. Sometimes it runs for weeks or longer fine and then it will freeze up a couple of times a day. Mildly annoying because it boots up quickly after reset. I thought it could be heat related but have nothing to back it up.

---

### Post by bbp on 2010-06-07
I have the same problem, Dell Mini 9 with Dell Ubuntu Remix install (the Ubuntu version that came with it)

I discover that it freeze more often when I'm not using it, when the computer is idle.

Thanks for testing it with that many OS, that's something I can not do because I don't have an external CD reader.

I also discover recently that a software called Maximus is responsive for 90% of annoyance I had from my computer. I really like it since I remove that software. Basically, what it does is:
* Maximise all possible windows, causing many applications to be simply impossible to use,
* Managing the Wireless connexion, and it is VERY bad at it (adding wl in /etc/modules solve that problem and I now able to connect to internet strait away at boot, with almost no delay)
* Steal windows focus in a VERY aggressive way (you have to click on the new window to be able to go to an other window, or else the new window will just popup over it again and again)
* Probably more...

That crappy software (maximus) is made by Dell so I was thinking that the instability was due to an other unwanted crappy Dell software. Since you test it with fresh install, at lease, now I know that it is not the case.

Bbp

---

### Post by bbp on 2010-06-07
Vickoxy tried to reinstall is Dell Mini 9 with an other Desktop environment (xubuntu and fluxbox)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1235388&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1235388&page=2)

He said that's solve the problem. As I said on my previous post, I can't reinstall the OS for now. If you try that, tell me if it's better. I have been using KDE for a while and I don't think I will go back to it. I'm happy with gnome.

Tell me if you try it, I'm curious...

[edit]
Oh, I just realize that the page I point you out propose a solution with xorg.conf (post #21)
---------
adding this line in my xorg.conf in section "Device":

Option "FramebufferCompression" "false"
---------
 

  I'm tried and it's fine so far... but it is s bit early to say Victory...

[edit]
from an other post:
[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/cb727ee73bcda913?pli=1](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/cb727ee73bcda913?pli=1)
---------
you might try if the lockups go away if you put this line into the 
 device section of /etc/X11/xorg.conf: 
 
Option "FramebufferCompression" "off" 
 
If it solves the problem, then you are hit by a bug that is solved in 
 version 2.4 of the intel driver. 
---------



I have version 2.2 according to Synaptic

---

