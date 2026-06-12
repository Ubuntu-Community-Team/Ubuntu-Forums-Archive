---
title: "Unsupported Dell? Fresh Ubuntu, Nothing works!"
date: 2008-11-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BastardNamban on 2008-11-19
Hi, I read the sticky before I posted, and it and its links weren't much help. I'm totally new to linux, just installed 8.0.4.

I have a Dell Inspiron 9300, and it came with XP. I've had it 3 years, and I wiped the HDD, and put a fresh install of 8.0.4 on, and obviously internet seems to work. But my sound is messed up (see post here: [http://ubuntuforums.org/showthread.php?t=984052]("http://ubuntuforums.org/showthread.php?t=984052"))

I know I need drivers, but Dell's site has no support I can find for anything other than Windows. No drivers if linux. I know there are customized HH images for Dell users, but they don't seem to have any drivers in them.

I found out how to get an html of my computer's hardware, so I know *what* I have, but no idea where to get any drivers to get my computer working!

If I'm missing something totally obvious to everyone who knows what they are doing, sorry- I've got no clue, and no one here abroad to talk to that could help. I have to rely on these forums.

How do I make all my stuff work? Please help!

---

### Post by notwen on 2008-11-19
The custom Dell images only provide the additional drivers/packages for their N-Series models(ie. Models that came pre-installed w/ Ubuntu).  I don't believe your Inspiron 9300 was one of these.  =]

If you're currently using the custom Dell images, I suggest re-installing using the basic [Ubuntu install]("http://www.ubuntu.com/GetUbuntu/download").  After that, look for a update notification on your top panel near your clock.  Install all available updates then post back w/ what is/isn't working for you and we'll work on getting your system up & running properly.  =]

---EDIT---
Looking at your audio post, Intel generally is well covered/supported in Linux so hopefully it won't be too difficult of a fix.

---

### Post by BastardNamban on 2008-11-19
Thanks for being so kind and straightforward. I've been trying to use the update function, which is a bright red ! arrow right now, but I cannot update ANYTHING, Ubuntu, firfox, flash ability, nothing works.

See this post why- [http://ubuntuforums.org/showthread.php?t=987044](http://ubuntuforums.org/showthread.php?t=987044)

I keep getting some sort of error message denying me ability to update. Even being a new user, I'm reading FAQs and stickys like mad, and I figured out how to bug report with launchpad. I reported the bug, but I still don't know how to fix it. Thus, I'm stuck.

Oh, and by the way- I'm using a standard 8.0.4 edition of Ubuntu, not a custom Dell image. I found out about the custom images, but didn't use them, as I saw they would be no help.

I would kill for a real guru here in person right now, but I'm in Japan, and even though I speak Japanese, no linux gurus here that I can find!

---

### Post by timcredible on 2008-11-19
why did you install 8.04?  install 8.10 instead, it has newer drivers (because it's 6 months newer than 8.04).  then update the thread with what (if anything) doesn't work on your pc.

---

### Post by BastardNamban on 2008-11-19
I installed 8.0.4 because it is the current long term support version. I'd prefer not to have to reinstall everything after Ibex goes the way of the Dodo- 2 years is too soon for me.

That said, See above post's link- I cannot update ANYTHING because of some kind of error, and I have no idea how to fix it.

I am stuck.

---

### Post by notwen on 2008-11-19
Can you copy/paste said error here?

---

### Post by BastardNamban on 2008-11-19
This is the error I get in update manager.

AN ERROR OCCURRED : "E: base-files: subprocess post-installation script returned error exit status 123"

A part of it says:
"cannot dereference /etc/dictionaries-common/words..".no such directory

I WISH the damn computer would let me copy and paste the error text, but copy & paste only seem to work in Firefox as CTRL+C/V, and even after figuring out Linux Cut & Paste is CTRL+SHIFT+ C/V, it lets me highlight the text, but NOTHING lets me copy the text! This is really annoying. I have no clue how you are supposed to get a log copied when there's a problem.

I even tried screenshot, but GIMP confuses the hell out of me- I can't figure any of it out to edit a small portion that had the error message.

Sorry, that's the best I can do.

---

### Post by BastardNamban on 2008-11-19
I got info now. Fortunately, I got the error directly from the terminal this time, instead of an uncopyable box text.

Here is the bug- I was trying to install GPM, something I found to (ironically) let me copy & paste error messages from terminal error boxes, and I got this- (it looks almost exactly the same as the update manager error, if not BEING exactly THE SAME):

______________________________________________
The following NEW packages will be installed:
gpm
0 upgraded, 1 newly installed, 0 to remove and 165 not upgraded.
1 not fully installed or removed.
Need to get 382kB of archives.
After this operation, 725kB of additional disk space will be used.
Get:1 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) hardy/universe gpm 1.19.6-25ubuntu1 [382kB]
Fetched 382kB in 1s (267kB/s)
Preconfiguring packages ...
Setting up base-files (4.0.1ubuntu5.8.04.3) ...
find: /var/cache/fonts: No such file or directory
find: /var/cache/anthy: No such file or directory
find: /var/lib/locales: No such file or directory
chgrp 0 /etc/dictionaries-common/words /etc/dictionaries-common/default.aff /etc/dictionaries-common/default.hash
chgrp: cannot dereference `/etc/dictionaries-common/words': No such file or directory
chgrp: cannot dereference `/etc/dictionaries-common/default.aff': No such file or directory
chgrp: cannot dereference `/etc/dictionaries-common/default.hash': No such file or directory
dpkg: error processing base-files (--configure):
subprocess post-installation script returned error exit status 123
Errors were encountered while processing:
base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)
(User@ComputerName):~$
__________________________________________________ ___


Here are the specs for my sound card, perhaps this has a connection to all
this? (another user sugguested a link) I'm worried- NotWen, you say intel is well supported, but I don't see any driver support for ICH6 Family Intel controllers anywhere on the Dell Linux wiki, or elsewhere. Am I missing something? My speakers are all out of whack- the sub is unaffected by the volume buttons on the front of the laptop, but the front speakers (treble) are, and adjust without connection to the sub. Muting works, but only on the front two speakers. It sounds really weird, thus.

__________________________________________________ ___
id:
multimedia
description: Multimedia audio controller
product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
vendor: Intel Corporation
physical id:
1e.2
bus info:
pci@0000:00:1e.2
version: 03
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration:
driver = Intel ICH
latency = 0
module = snd_intel8x0
_____________________________________________

I'm kinda crowd sourcing this- [http://ubuntuforums.org/showthread.php?t=987044](http://ubuntuforums.org/showthread.php?t=987044)

The same problem, 2 different posts! Sorry.

I kinda see why a lot of folks get turned off linux, fast- I was an XP master, could do anything even in BIOS, but I'm losing my damn mind here in linux- I can't even get basic stuff working with this error!
This is not as easy as many friends and others posit Ubuntu to be. I have to go to sleep now, it's 230 am my time. I'll check back in like 9 hours.

---

### Post by BastardNamban on 2008-11-20
--------------------------------------------------------------------------
UPDATE-

I used a bit of magic, and the error is gone. I found out it comes up only if, upon a fresh install from the live CD, you don't wait for the updates to appear, and directly go into firefox. I don't know why, but that screwed things up, and locks up updating.

So to anyone else who got the above error- that's what you do. Fresh install, WAIT for the updates- don't use teh internets. After updating will complete with no problems, reboot, then try firefox. Updating your media codecs et al should work now.
--------------------------------------------------------------------------

I still have speaker problems. I noticed, though, finding the vertical volume in TOTEM video player, there is something interesting.

The front buttons on my laptop had linked the mini sub and both front speakers (mid/treble) when I used windows XP. The sound adjusted equally up or down on all speakers together from the front buttons, and the same when I adjusted the volume in winamp.

BACK TO UBUNTU- I opened a Mad Max music video .wmv I had on one of my external NTFS drives, now working fine. The front buttons for sound still adjust only the front 2 speakers- the sub is unchanged. HOWEVER- in TOTEM, adjusting the volume with the vertical bar EQUALLY raises and lowers the front & sub speakers!

If I adjust the 2 treble speakers to low volume, with the sub unaffected, 
and then raise the volume using the TOTEM bar- it will raise the sub even louder, but it also raises the front two speakers. If I lower it in TOTEM, it lowers both.

Basically, the front buttons in the past were synced in XP, but now they are not- the sound adjusts properly only if done from within TOTEM. I want the buttons to work in sync independant of the media player like they used to in XP. How do I do that? As it is- this may be cool, as I can now actually adjust treble & bass independantly using the front buttons, but being able to link them again would be nice too, if I need it again. Am I missing the point, and this is how it's supposed to work, and I don't get it?

---

### Post by buddyd16 on 2009-01-08
In the sound properties dialog you need to link the main volume with the laptops' bottom bass speaker by holding control and clicking each item, from what I can gather in my limited exposer to linux this basically tells ubuntu that when the main volume is adjusted the linked components should adjust also. I am in the process of installing ubuntu 8.10 now and will post a more detailed explanation once that is up and running.

---

