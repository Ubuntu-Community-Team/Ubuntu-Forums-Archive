---
title: "strange memory consumption values in System Monitor"
date: 2008-05-05
forum: Desktop Environments
---

### Post by s_raghu20 on 2008-05-05
Hi,

on my hardy 64bit, I get this very strange set of memory consumption values for some processes. For some others its looks fine (I am not sure anymore if those values are correct anyway).

Attaching a screenshot.

Has anyone seen a process in their system monitor that takes up **17179869180.0 GB RAM** ??

---

### Post by swankyfb on 2008-05-05
i have had a similar problem with this, but instead, it says that i was using 100 percent of my cpu. it must be a bug, especially when i have equipment capable of running linux, its an amd 3000+

---

### Post by RAOF on 2008-05-05
The "insane memory usage" problem is an Xgl bug.  The sooner we can drop that unmaintained annoyance, the better.

If system monitor says CPU utilisation is at 100%, it's likely correct.

---

### Post by s_raghu20 on 2008-05-06
> **RAOF said:**
> The "insane memory usage" problem is an Xgl bug.  The sooner we can drop that unmaintained annoyance, the better.

If system monitor says CPU utilisation is at 100%, it's likely correct.

Well, for me its says 50% CPU, but I guess that would be because I am on Core2Duo, and system monitor shows 2 cpus in there. So, effectively its hogging 1 cpu 100% resulting in effectively 50% usage overall.

How about a bug reported on this issue ? Is it already reported ?

---

### Post by retrow on 2008-05-06
Instead of using the graphical system monitor, use the command line based htop
```
sudo apt-get install htop
```
There is a  bug in system monitor itself. Running htop on command line yields accurate reading of your system.

---

### Post by RAOF on 2008-05-06
> **s_raghu20 said:**
> Well, for me its says 50% CPU, but I guess that would be because I am on Core2Duo, and system monitor shows 2 cpus in there. So, effectively its hogging 1 cpu 100% resulting in effectively 50% usage overall.

How about a bug reported on this issue ? Is it already reported ?

What issue?  What program is taking 100% of a core for you?  This can be entirely normal if, for example, that program is doing something fundamentally CPU intensive :).

---

### Post by s_raghu20 on 2008-05-06
> **RAOF said:**
> What issue?  What program is taking 100% of a core for you?  This can be entirely normal if, for example, that program is doing something fundamentally CPU intensive :).

The point was about system monitor showing insanely huge memory consumption values for processes.

The CPU usage that I reported was for gnome-display-properties thing.  I think I confused between two threads and mentioned my cpu usage stats here, whereas they were meant to be taken in the view of this thread - [http://ubuntuforums.org/showthread.php?t=783619]("http://ubuntuforums.org/showthread.php?t=783619")

So, back to the system monitor thing, how is it supposed to be fixed then ? The fact that it reports wrong values for memory used remains. Has it been raised as a bug ? Is there some update/fix already available ? Or is it just because I am using xserver-xgl ?

---

### Post by retrow on 2008-05-06
You can report the bug at [Launchpad](https://bugs.launchpad.net/). If it has already been reported, you will be directed to the thread where people are discussing/debugging the cause and nature of this bug while working on a fix at the same time.

---

### Post by RAOF on 2008-05-06
It's already been reported here: [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xgl/+bug/148325](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xgl/+bug/148325).  A good workaround is generally to remove or disable[1] Xgl - almost everyone doesn't need it :).

[1] To disable Xgl, create a file called 'disable' in ~/.config/xserver-xgl

---

### Post by s_raghu20 on 2008-05-06
> **RAOF said:**
> It's already been reported here: [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xgl/+bug/148325](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xgl/+bug/148325).  A good workaround is generally to remove or disable[1] Xgl - almost everyone doesn't need it :).

[1] To disable Xgl, create a file called 'disable' in ~/.config/xserver-xgl

Thanks for the pointer.

Though I dont mean to be critical, but the overall situation about this bug looks strange.  On Gnome, its marked as RESOLVED, and still we are facing it in latest gnome build in hardy. There it says in Resolution tag as NOTGNOME, which I interpret as gnome team deciding that its not a gnome bug.

anybody knows where to track it further ? who develops/maintains that package ?

---

### Post by RAOF on 2008-05-06
GNOME is correct; it's not a GNOME bug.  It's a bug in the way XGL reports memory usage.  It should be reported upstream to the freedesktop.org bugtracker, but there's not much development of XGL going on anymore - there have been only 9 commits to the repository this year so far, and fewer than 30 commits over the whole of 2007.

> **RAOF said:**
> ...The sooner we can drop that unmaintained annoyance, the better.
...

It's not quite unmaintained yet, but it's pretty much obsoleted by the improved Xorg drivers, EXA maturing, DRI2, etc.

---

### Post by s_raghu20 on 2008-05-06
> **RAOF said:**
> GNOME is correct; it's not a GNOME bug.  It's a bug in the way XGL reports memory usage.  It should be reported upstream to the freedesktop.org bugtracker, but there's not much development of XGL going on anymore - there have been only 9 commits to the repository this year so far, and fewer than 30 commits over the whole of 2007.

It's not quite unmaintained yet, but it's pretty much obsoleted by the improved Xorg drivers, EXA maturing, DRI2, etc.

Right, I think I got the picture. I am using a package that is not developed actively further.  

My need to use this driver is because of my laptop hardware (HP Compaq 6710b). As of now, I found out that only with this driver Compiz works on my laptop.

It would be interesting to check out the possible replacements for xgl on my hardware and see how they behave.

---

### Post by RAOF on 2008-05-06
> **s_raghu20 said:**
> Right, I think I got the picture. I am using a package that is not developed actively further.  

My need to use this driver is because of my laptop hardware (HP Compaq 6710b). As of now, I found out that only with this driver Compiz works on my laptop.

It would be interesting to check out the possible replacements for xgl on my hardware and see how they behave.

Really?  For almost all people Hardy should have removed the need for XGL to run compiz - presumably you have an ATI card in that laptop?  If it's supported by the fglrx driver, you don't need XGL.  If it *isn't* supported by the fglrx driver, you can use the open-source 'ati' driver (possibly having to bypass compiz' blacklist, though).

---

### Post by s_raghu20 on 2008-05-07
> **RAOF said:**
> Really?  For almost all people Hardy should have removed the need for XGL to run compiz - presumably you have an ATI card in that laptop?  If it's supported by the fglrx driver, you don't need XGL.  If it *isn't* supported by the fglrx driver, you can use the open-source 'ati' driver (possibly having to bypass compiz' blacklist, though).

Well, I am quite sure that I dont have an ATI card in the laptop, its an HP Compaq 6710b, and from knowledge the graphic card is from intel their 965 series.

Anyway, I'd try removing xgl driver and give it a shot.

will report.

[Edit] Just did that. Removed xserver-xgl package from the system, logged out and back in. Now, Compiz still runs fine (I normally use only one feature and that looks ok), also the memory usage values in system monitor look ok. No processes consuming umpteen zillion bytes of memory.. :)

Thanks for the tip RAOF..:)

---

