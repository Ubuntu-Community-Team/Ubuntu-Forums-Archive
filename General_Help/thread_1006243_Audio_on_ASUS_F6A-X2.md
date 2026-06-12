---
title: "Audio on ASUS F6A-X2"
date: 2008-12-09
forum: General Help
---

### Post by xquercus on 2008-12-09
Having great success with Ubuntu 8.10 on a new ASUS F6A-X2.  There is very little information available regarding this notebook and Linux compatibility.  Everything from video, the webcam, to power management works with Ubuntu out of the box -- with the exception of audio.

The F6A-X2 has an ALC662 audio controller which uses the snd_hda_intel driver.  Out of the box, audio doesn't work.  By adding the following to /etc/modprobe.d/alsa-base, I was able to enable audio (recording and playback):

options snd-hda-intel model=eeepc-ep20

The model operand can take any of a number of values:

3stack-dig
3-stack
3stack-6ch
3stack-6ch-dig
6stack-dig
lenovo-101e
eeepc-p701
eeepc-ep20
auto

My choice of eeepc-ep20 was based on the assumption that both the eeepc and this F6A have a relatively simple audio setup.

Questions...  Is another operand more appropriate?  How does one plug in with the ALSA folks to insure future versions of ALSA will properly automatically detect the proper "model"?

Thanks!

-Jeff

---

### Post by TheMemphisExperience on 2008-12-18
Okay, I just got one a few days ago and I Love the machine. It is really great that Best Buy saw fit to put on clearance the one item I wanted from them.

Anyway, I too encountered the sound problem. To what part of the file do I add that line of code to? I had added it in a LiveCD environment, but it would not work. I am now running 8.10 as a guest OS in VirtualBox under Vista to try to work out the bugs. Is a reboot required?

As for your suggested fix for the future, you could try Launchpad.

---

### Post by TheMemphisExperience on 2008-12-20
I added the line where I thought it should go, at the end of the options list while under virtualbox. But still no sound. Unfortunately, the use of virtualbox introduces the question of whether or not sound even works in it normally. 

But I still don't know if I did it right anyway. I'll have to get a second computer.

Before I unpack the trusty Acer, though: help?

---

### Post by TheMemphisExperience on 2008-12-22
Solved for me as well. I think the issue is one related to all HDA Intel ALC662 cards. I did a search for the card and got back results from several people experiencing the problem from several manufacturers, but just one card. Their solution is similar, but uses: 

options snd-hda-intel model=m51va

This is added at the very end of /etc/modprobe.d/alsa-base. After a restart, I had to change some levels in ALSA's GUI, but sound worked just fine. Switches worked as normal too.

---

