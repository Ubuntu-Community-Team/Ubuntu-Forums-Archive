---
title: "Blank screen after system video test"
date: 2009-11-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cccddd on 2009-11-10
Hey guys (and gals),

Here is my issue, its another blank screen!  Yes i know, there are a million of these.  I did some research on this forum and it seemed to me that many of the questions werent very specific, thus resulting in hard to diagnose issues.

My issue is VERY specific.  I know exactly what I was doing.  Hopefully one of you has had the same problem and can point me in the right direction.

I installed Ubuntu 9.10 on my dell dimension 2400 last night.  Everything was working.  I ran the updates, installed the flash plugin for firefox and then decided to browse my new operating system.

I went to System --> Administration --> System Testing  (im not exactly sure these names are correct, as i am going by memory here).  I went through a few of the tests and came to the video test.  I dont know why i had to test this, since it was working fine but i decided to run the test.  It then began testing all these different resolutions and the last resolution was all black or blank.  

I left it alone for a few minutes....nothing.  I turned off the computer with the power button and restarted it.  All i see now is the ubuntu logo? but no splash screen or login screen, it goes black before i can do anything.

So I did some research on google and stumbled upon a post with a similar problem.  The advice was to restart in recovery mode and type "sudo dpkg-reconfigure -phigh xserver-xorg"....this didnt work for me.

Another guy said to load recovery mode and type "sudo nano etc/X11/xorg.conf" and change the drivers or something.  you can find it [HERE]("http://ubuntuforums.org/showthread.php?t=1054450&highlight=BLANK+SCREEN+AFTER+TEST&page=2") .  This didnt work either.  Hopefully some of these changes i am making arent making the problem worse.

Basically, I am about to reinstall and try again.  I hate to do that because Ill never learn how to fix this issue and if it happens again ill be in the same boat.

Sorry for the long post, hopefully one of you can help me figure this one out.  Thanks in advance!

Rob

---

### Post by thedib on 2009-11-11
I could use some help with this one too.  I ran into the exact same problem.  The first time it happened was random.  I had left the system on for the day after a fresh install and then added updates from the update manager.  I also installed the flash plugin for Firefox.  After watching a youtube video I walked off for a few minutes and when I came back I encountered the black screen.  I turned the computer off and turned it back on and I would only get a black screen after Ubuntu loaded.  I tried reinstalling the OS and running the tests and everything was fine until the last part of the video test.  Then I was stuck with a black screen again.  Tried running the test again from the disk and still got the same results.  Seems like there is some type of mode that Ubuntu is accessing that the Dell 2400 video card doesn't support.  I just don't know for sure what it is.

---

### Post by Databit on 2009-12-03
This sounds like it might be the same issue I'm having with xubuntu or ubuntu 9.10 on a Dimension 2400. Anyone know how to get to the System Test/Video test in xubuntu? 
Or better yet how to change to the vesa driver if there is no xorg.conf file?

---

### Post by cybrsaylr on 2009-12-05
Same thing just happened to me after doing the required restart after today's updates to the newest 2.6.31-16-generic Kernel a few minutes ago. This restart took longer than usual, like it was going though some scan. On restart monitor screen went black, then posted a frequency problem. My new Dell listed in my sig line below was running but screen was black. Did a hard restart and again, it took longer than usual to restart, then was a bit slow and using more ram than usual for just idling, 1.3GB ram instead of the usual ~350-400megs of ram at idle. I then did another normal reboot which took the normal reboot time of 42 seconds and all looks normal again.

Hoping whatever happened was cleansed out in the reboots. Am now using the newest 2.6.61-16 Kernel and all seems normal again. The previous two 2.6.31-14 and 2.6.31-15 versions ran great with no issues.

---

