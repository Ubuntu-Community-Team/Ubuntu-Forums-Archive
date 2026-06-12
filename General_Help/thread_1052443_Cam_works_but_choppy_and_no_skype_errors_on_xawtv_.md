---
title: "Cam works but choppy and no skype errors on xawtv help"
date: 2009-01-27
forum: General Help
---

### Post by thrasher6900 on 2009-01-27
So I install xawtv and can capture video . .....but it's choppy and for some reason, I cannot even do a play back.

When I run Skype, none of my sound or video devices are detected.

What do I do?

I'm fairly new at this so you're help is greatly appreciated and I thank you all ahead of time

Cheers

---

### Post by spiderbatdad on 2009-01-27
for audio try setting the device manually in the skype options audio menu.
For video: [http://ubuntuforums.org/showthread.php?p=6529467](http://ubuntuforums.org/showthread.php?p=6529467)

---

### Post by thrasher6900 on 2009-01-27
> **spiderbatdad said:**
> for audio try setting the device manually in the skype options audio menu.
For video: [http://ubuntuforums.org/showthread.php?p=6529467](http://ubuntuforums.org/showthread.php?p=6529467)It sees the video device but the test shows a fuzzy screen.

Aright it works on the test.....but not on the call.  I get an audio device error.

---

### Post by cariboo on 2009-01-27
What version of Skype are you using, as I found the version in the Medibuntu repositories wouldn't detect my webcam either. I used [this guide]("http://ubuntuforums.org/showthread.php?t=432295&highlight=skype"), the skype package seems to be version agnostic, so it should work on a 32bit install too. 

I just copied the instuctions for Intrepid, and pasted them in a terminal and let it run. Once it was installed I started Skype and set the sound output to default and the input to the usb device listed in the menu. Everything works like a charm.

BTW Windows doesn't even detect the builtin microphone of the webcam, so I had to buy a seperate headset to use Skype in Windows 7.

Jim

---

### Post by thrasher6900 on 2009-01-27
I found this command and for some reason it makes the cam work.

But only if I use this command everytime.

> LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

But my sound devices are still not working with it, so I cannot reciev my call due to sound errors.

---

### Post by spiderbatdad on 2009-01-28
I sent you a link in the first response to your thread on how to video with skype. It includes that command, and instructions on how to create a small script and launcher, so you dont have to use the command everytime. Why dont you try actually reading the responses to your threads, then following the instructions.

---

