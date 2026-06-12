---
title: "How to get the audio codec STAC9227 to be installed in a dell inspiron 1525"
date: 2010-01-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by renjumace on 2010-01-09
Sorry to post a new thread again for the same problem. This time i decided to be more descriptive. After a lot of scrabbling i found out a link to help me out, [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting). But unfortunately, after all the steps described in the above mentioned source, i wasnt able to cure the problem. One possible solution is to obtain the Sigmatel STAC9227 audio codec required. Can anyone provide any possible source for this??.. Help needed! I am desperate.. otherwise i would have to switch to vista.

---

### Post by irishbreakfast on 2010-01-09
renjumace,
I too have a Dell Inspiron 1525 (18 months old) and have experienced sound problems, but it gets easier with each new Ubuntu release. And I haven't installed anything except the codecs to play various file formats.

Have you checked out the stickies in the Multimedia&?Video forum? They served me well.
Do you get any sound, like during boot?

---

### Post by renjumace on 2010-01-09
@irishbreakfast
there is no sound during boot up.. thats when i found out that movies also didnt had sound.. i somehow doubt whether installing codecs for individual video formats will help... does the new ubuntu, karmic koala fixes this issue... please reply..

---

### Post by irishbreakfast on 2010-01-09
I can't say if karmic will fix the issue as I am not sure what the problem is.
Yes, other codecs are not going to help at the moment - It was just a comment about my experience.
I have used 8.04, 9.04 and 9.10 with the sound working in each.

Have you looked at those stickies?
Have you checked that the volume is up to max?
Have you checked alsamixer?
What version of ubuntu?

---

### Post by irishbreakfast on 2010-01-09
sorry this is a bit long and before you had a chance to reply. It's been a long night and I wanted to send this before I slept in the hopes it will help you.

i've been looking at the community docs you used and there is a lot there that I never needed to do (like modprobe). I only mention because we have the same machine.

The cmd 'speaker-test' is useful, it is a quick way to test without concern about the source file and codecs. 
$speaker-test -Dplug:surround51 -c6

My notes on jaunty show that I had to do this when the sound stopped working. It looks like it just does a clean install and runs alsamixer to set the volumes to max.
[INDENT]sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install  linux-sound-base alsa-base alsa-utils
aplay -l
alsamixer
sudo apt-get install asoundconf-gtk
asoundconf-gtk[/INDENT]

Curiously, I have no notes for karmic, so it must have worked right out of the box. Although I don't like the sound preference application.

FYI, I have:
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by renjumace on 2010-01-11
@irishbreakfast
                      thanx for the post man. but unfortunately the problem wasnt cured. the sound during logging on came when i tried out one of the replies on one of my previous threads. but again i had to format my system again as i was not able to install the updates.. so in the end i decided to try that post once again and then maybe install any other codec or may use wine to install vlc player or something... anyways thanx for ur time man.. really appreciate it.

---

