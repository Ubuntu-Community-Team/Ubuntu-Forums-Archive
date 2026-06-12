---
title: "High CPU usage (nautilus)"
date: 2006-12-11
forum: Desktop Environments
---

### Post by jweb on 2006-12-11
New to Ubuntu and Linux in general - but learning quickly.  I run Ubuntu 6.06 on my laptop with the Gnome desktop.  I have recently noticed that nautilus is eating up to 80% of my CPU cycles ONLY when I open a file browswer window pointing to a partition mounted as "/media/warehouse":

/dev/hda4       /media/warehouse vfat    defaults,utf8,umask=007,gid=46 0 1

If I simply back out to /media or to the root file system (or any other subdirectory in the file system), the CPU usage immediately drops to 0 (or slightly above).  It seems too coincidental that viewing one partition causes insane CPU usage... but I don't know enough about Linux to begin to understand why.

I don't think this is related to the bug I have seen documented in other threads here on Ubuntuforums - that describe high CPU utilization when dragging a window.  As I say, it is specific to pointing to a specific directory.

I have only recently noted this problem - which leads me to believe that I made some change that has caused this.  Did I diddle with the mount options erroneously in /etc/fstab as printed above?

Thanks in advance for the help...

JWeb

---

### Post by Henry Rayker on 2006-12-11
wtf?! ad-spamming bot?

As for the absurdly high CPU usage, I've found nautilus to be quite...sketchy, in terms of CPU usage. Sometimes, it'll just ramp up to 100% and stop responding, sometimes it'll be stable for a week straight.

I can't see anything wrong in the fstab, but I'm far from an expert.

On a different note, the taxing cpu and memory usage by nautilus is one thing that encouraged me to seek out new desktop environments and file managers.

---

### Post by Judicata on 2006-12-11
The CPU thing is a known bug.  It happens to me when I open a folder in nautilus in which a file is being downloaded.  I remember seeing a bugfix for this, but it involved steps I didn't want to take at the time.  Sorry, I really don't have time to hunt it down right now, but if you search around I'm sure you can find it.

Until then, just run something like "top" in a terminal, and kill Nautilus.  It will restart at normal CPU usage.  And you won't have to reboot or restart X or anything. (Open a terminal, type "top" then look for the PID for Nautilus. type "k" and enter the pid, then hit enter).

---

### Post by K.Mandla on 2006-12-13
(Removed spam post. Making the world safe for Ubuntu users, one post at a time. :D )

---

### Post by raydar on 2008-01-08
I have a similar problem (not related to logging out and back in, see [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471) ) which seems to share something with Judicata's post above:

I download a flash video to my desktop, and when the download stops, I right-click and hit Properties to check its size.  Instead of immediately getting a Properties box, I get a "now creating properties box, you can stop this action by clicking Cancel"-type dialog.  Several minutes later, that dialog goes away and I get the Properties box.  In the System Monitor, Nautilus shows up with cpu usage maxed, and my system becomes extremely slow.  This seems to happen only with the flash video file I downloaded; I can right-click and hit Properties on other files on my desktop without Nautilus throwing my system into "molasses mode."  

I thought maybe it had to do with file size, since the video was 200MB and the other files I tried were much smaller; but it can't be a mere size-calculation thing, because I can open a Nautilus folder window displaying the files on my desktop without causing the problem, and it appears right away with the size displayed (in list-view mode).

Anyone else still having similar issues (I see the last post in this thread was a year ago)?

---

### Post by alx010 on 2008-01-08
I had the same problems with Nautilus, cpu usage, & the 'creating properties' dialog. I finally installed the Xubuntu desktop, & found it worked much better on my computer.

---

### Post by rune0077 on 2008-01-08
Try to keep top or System Monitor running in an open window while using the system. This way you can see from the list exactly what process is eating up the CPU.

---

### Post by raydar on 2008-01-09
Wow, thank you for mentioning top; I'd never heard of that, and yesterday I had a few choice words for the System Monitor, which showed my processor maxed while the percentages of the processes it listed didn't add up to more than 10 or 20%.  When I ran top, I immediately found that my Boinc client was the hog as far as processor percentage--I just couldn't see it in System Monitor 'cause it was running as a different user.

So, I tried opening a properties box for the flash video I'd downloaded to my desktop, in order to reproduce the problem, and watched Top.  My system didn't slow down right away, and a properties box appeared after "only" 10-15 seconds.  I've generally been running Firefox and vmware server during the time I've experienced this problem, and I already had Firefox running to download the file; I started vmware, and within half a minute after it was up and running, my mouse was all jerky and operations inside and outside of the vmware virtual machine were creeping along.  Nevertheless, boinc was the only processor hog according to top & System Monitor.  Nautilus was using a fairly small amount of resources, and so was vmware; Firefox isn't exactly frugal with memory, but it wasn't using much processor either.  

I then opened the boinc client and paused it, and that took its processor percentage way, way down; my mouse pointer no longer jerked around in fits & starts, and general system/gui sluggishness was reduced, but moving windows around the screen, opening menus, etc., was still pretty slow, including inside the vmware virtual machine.  So,  I shut down vmware to see if that would speed things up.  The result was inconclusive, better than molasses, but system still not full speed.  I then un-paused boinc to see if that would slow things way down again--but again inconclusive, 'cause it didn't.

Right now, after all the above, I have boinc, vmware, Firefox, System Monitor, and top running, and system performance is still moderate, neither excruciatingly slow nor at full ordinary speed.  Trying a properties box on the flash video file on my desktop, I still get the "creating properties box" dialog for maybe 10-15 seconds before a properties box pops up, and that's a full minute faster than yesterday before I wrote my earlier post in this thread.  So, I'm afraid I'm scratching my head--boinc and vmware seem like suspects in the crime, but top shows vmware never hogging the processor or memory (about 15% cpu, 4.3MB memory), and while boinc tends to hog the processor, pausing it didn't immediately remove the sluggishness problem (not like flipping a switch, anyway).  I'm starting to think the properties box thing is a symptom, not an indication that Nautilus is the problem.  I hate it when things are this squishy and keep me from nailing down some particular culprit. 

Oh well, I ordered some more memory the other day; that'll take my AthlonXP 2200+ machine from 512 to 1024MB of RAM; maybe that'll help.  I appreciate the suggestions--I don't really want to switch to Xubuntu . . . I'm running UbuntuStudio, though, and it's possible that one tweak or another that UbuntuStudio comes with is contributing to the problem condition here; I just don't know.  One thing's for sure: I can't believe I switched from WXP to Ubuntu a couple years ago but only just now found out about top!

---

### Post by raydar on 2008-01-11
Well, this morning I didn't download a thing, but just tried opening a properties box on a flash video file via right-click.  The system slowed way down again, and top and System Manager showed Nautilus to be the culprit; it was consuming approx. 148MB of RAM, and I didn't have more than two file browsing windows open; vmware and Firefox and boinc were running, but none of them were consuming all that much in resources.  I'm thinking there's got to be something about the Flash video files involved in this; I just wish I knew what.

---

### Post by itismike on 2008-03-04
Having the same symptom here.  The only thing I can imagine might have caused it was that I inserted a CD and tried to open an .htm file.  Nautilus prompted me if I wanted to 'run  or display' the file and I chose 'Display'.  It never did respond, so I did it again.  Nada. I gave up on reading that CD.  The CPU usage spiked on Nautilus about 45 minutes later.  All Nautilus windows had been closed long ago.  I had been using rDesktop extensively.

Killing Nautilus only resolved the problem temporarily.  Nautilus self-spawns immediately.  I can close the window, but the process seems to continue to self-generate, and climbs back up near 100% usage.  I tried killing all processes, and will now try to kill the desktop session and login again.

---

### Post by itismike on 2008-03-04
killing the session and a reboot made no difference.  It still maxes out with huge CPU utilization.

---

### Post by raydar on 2008-03-04
This is just a stab in the, well, twilight, but:  I've subsequently gotten a new, second machine, and on one of its drives I installed the same OS configuration I have on my other computer, the one that had/has this problem. The problem hasn't occurred (yet) on the new machine, and I'm thinking the difference could be either (1) that it's a fresh install of Gutsy, while the computer with the problem at issue was an upgrade from Feisty to Gutsy, or (2) that it's a fresh install, period, of Nautilus in particular.  I'm not saying reinstall your OS per #1, but per #2, maybe a "reinstallation" or ordinary "removal" or "complete removal" (and then installation) of Nautilus could help.  "Complete removal" removes all configs/settings, as I understand.

On my machine that had/has this problem, I haven't been plagued by it in a long time, and what I've been doing is keeping whatever folder a file is downloading into closed as much as possible.  I open it to move the file or check & see what its size is, but otherwise as a rule I keep it closed, and I don't use the desktop for downloading anything big 'cause it can't be closed. I wish I could say I know for sure that's directly related to the problem's not happening.  

I've also been keeping such folders closed on my new 2nd machine out of paranoia, which sucks to find myself doing, but on the occasions when I've accidentally left a downloaded-to folder open for the whole time I d/l something large, the problem still hasn't replicated.

---

### Post by gray380 on 2008-03-13
Hello All!

Is there any solution to solve this problem?

I have no fresh installation (only upgrades from 5.10) and I have this annoying problem with nautilus high cpu usage approximately with half-year.

brg,
Serhiy.

---

### Post by gray380 on 2008-03-17
Seems like  I found how to solve a problem. 
I deleted all of files from a ~/.nautilus directory and problem no longer observed.

> **gray380 said:**
> Hello All!

Is there any solution to solve this problem?

I have no fresh installation (only upgrades from 5.10) and I have this annoying problem with nautilus high cpu usage approximately with half-year.

brg,
Serhiy.

---

### Post by eeried on 2008-05-19
Same problem with Hardy Heron even after deleting content of ~./.nautilus

I had no problem with Gutsy. I'm thinking of installing Thunar but as Nautilus is perhaps too much part and parcel of Gnome to be safely removed.

---

