---
title: "Ubuntu 7.04 on Dell XPS 710 - no go"
date: 2007-07-27
forum: Dell  Ubuntu Support
---

### Post by shredsalot on 2007-07-27
I have a brand new XPS 710 that I'm trying to put Ubuntu on.  When I boot off the CD, I get to the menu where I can select "Boot or Install Ubuntu".  I then get a nice black screen with an orange progress bar that starts (very slowly) ticking down.  Then, the whole thing sort of smears with video artifacts everywhere and the system completely locks up.  I'm suspecting that the video drivers on the DVD are insufficient to drive the GeForce 7950 GX2's due to the corrupted display, but I have no idea whats really going on.  Has anyone else managed to get this to work?  How can I work around this driver problem?

---

### Post by Rocket2DMn on 2007-07-27
If the LiveCD doesn't work, you can try the alternate cd which gives you a text based install
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check the box for Alternate CD at the bottom before proceeding.
After the download is complete, check the md5sum
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against.
Then burn to a cd at a slow speed, like 4x.  Use quality media if you can.

Once you have the install complete you will be able to fiddle with the drivers more, if they are still a problem.

---

### Post by shredsalot on 2007-07-27
Well, I'm a little concerned about the prospect of mucking with drivers too.  

I have another box (one I built myself - non Dell) that Ubuntu installed on first go.  But, it occasionally dies to a black screen of death (at least it's not blue) where all you see is a mouse pointer; nothing you do will bring back the UI unless you reboot.  At least with windows, it's man enough to give some sort of mesage when it shits the bed.  Anyway, I suspect it's a problem with the video driver (Nvidia GeForce 7, SLI, etc.) because it tends to do this from 3D screen savers, going into power save mode, or when desktop effects are enabled.  

I have the restricted driver that was installed automatically out of the box. Not knowing what version of the driver this is (no way to find this out in the driver list), I figured I'd just go to the Nvidia website and download and install the latest driver like I do every 2-3 weeks on my windows box.  Not going to happen.  First, it took me forever to figure out how to su root (it didn't like any password I gave it, I thought the first user was supposed to be root; ah well, went into the user manager and brute forced root password to what I wanted it to be - please tell me it wasn't blank by default!!!).  Anyway, got through that, and now the installer wants me to exit xwindows before I install it.  WTF.  I've been trying to figure out how to get into console mode for about 12 hours now to finish this install on the slight chance it might fix the problem with the persistent crashing.

In any case, if this is the sort of crap a typical user with new-ish hardware has to go through to do something as mindlessly simple as running a video driver installer, linux is going no where fast.  I can't wait to try and get my sound card working next...

---

### Post by Rocket2DMn on 2007-07-27
The LiveCD doesn't work for a lot of people, it's not unusual.  Nvidia has better driver support in linux than ATI does, but most of us get adequate functionality out of them either with the open source drivers or by installing the restricted ones.  Some people also have trouble with soundcards, but that too can be troubleshooted if problems arise.

---

### Post by shredsalot on 2007-07-27
I'm running Nvidia cards (SLI).  What version of the Nvidia driver comes on the DVD?  This might help me identify if this is the source of my failed install.

---

### Post by Rocket2DMn on 2007-07-27
Deleted Post -- Wrong Thread

---

### Post by Rocket2DMn on 2007-07-27
Here might be a place to start: [http://ubuntuforums.org/showthread.php?t=418805](http://ubuntuforums.org/showthread.php?t=418805)
That guy was able to get it to work.  He disconnected the second card during install, then put it back in later after updating the system.

---

### Post by razeshkale on 2007-10-11
Wait for 7.10 this will fixed your problems!
Cheers

---

