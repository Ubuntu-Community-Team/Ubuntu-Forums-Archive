---
title: "[SOLVED] Inspiron 1521 Webcam/Built In MIC"
date: 2008-06-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gmstalk on 2008-06-03
Has anyone had success with getting the built in Mic/Webcam to work on the 1521? 

I have never gotten the Mic to work and the webcam works sometimes (it works in cheese and ekiga when it wants to). 

I have followed several posts and did various thinks with ALSA and I am pretty sure I have done more harm than good. 

Anyone got this stuff working well?

I have had great success otherwise. I use ndniswrapper for wireless.

---

### Post by sanjuuichisandoichi on 2008-06-04
I have an Inspiron 1420 and presume that the webcam/mic are the same between these two models.

Webcam:  this simply requires things that can use the V4L2 plugin (not just V4L)  This is an option for programs like Ekiga and Cheese.  Many others (wengophone, camorama) simply don't have V4L2 support (hopefully this will change).

Mic: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work)
Try this fix, it worked for me.  The only issue was that the audio buttons didn't work after the patch.  That was also a simple fix though and is explained at the bottom of [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Analog_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Analog_Mic_Does_Not_Work)

Lemme know if these work for you.

---

### Post by gmstalk on 2008-06-04
Thank you for your reply. Unfortunately my arc it x86_64 not i386. So I am unable to install the necessary backports. I will poke around on the dell site and see if I can discover a solution. I did not think to look there until your post. 

Thanks again. If it were not for the people in this forum I do not think I would have gotten any of this to work. You are the people that make this whole think work.

---

### Post by svega85 on 2008-06-06
have you gotten this to work because i have a 1420 and the webcam works for a minute then stops working

---

### Post by gmstalk on 2008-06-09
After causings a major problem, and then a fresh install of Hardy, I have the mic, sound, and wireless working. Since this is about the mic, here is what I did.

I tried the backports for my machine (uname -r). I used Synaptic to find linux-backports-modules and found the one that matches the output of uname -r.

I followed the directions here:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Up to the reboot part, then used the relevant part of the section "No mic working, rest OK:" because I only run Ubuntu on my system. 

I used the latest alsa stuff 1.0.17rc1
I used "options snd-hda-intel model=auto" as the last line of /etc/modprobe.d/alsa-base 

To test I used the sound recorder. Ekiga also works. Yay!

---

### Post by oscarFrance on 2008-07-26
Hi,

Just for information, The following link gave me a solution for snd-hda-intel problems on a inspiron 1525:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade)

I had "Unresolved symbols" with snd-hda-intel when upgrading above 2.6.24-14.

I didn't change anything in alsa-base.

Best regards,
Oscar

---

### Post by PinkFloyd102489 on 2008-07-26
The webcam/mic array are the same in the Inspiron models. I have a 1720 and they didnt work on 32bit but work in 64bit.

---

### Post by patrickballeux on 2008-10-12
Hi,

The builtin microphone is working on my 1521 if I select the recording to Alsa and not pulseaudio (System-Preferences-Sound).  Also, open the sound volume applet, select the options tab, and select the "Digital 1" microphone.

Then play with the recording volumes.

Now, I modified my setup to use Pulseaudio and my internal microphone is "not" working anymore.  Actually it is, but the volume is very low and I am unable to raise it even if I do it in the sound volume applet.  But since I mostly use an external mic, I do not really care since the external mic is working as expected.

No patch, no nothing, just selecting Alsa as a recording source and setting Digital 1 as the microphone.

Now, the builtin webcam is a v4l2 and can work in Cheese, aMSN, wengophone and that's about it.  There is some success with Flash v10, but the flash player is sometime crashing and you have to reboot to regain control of the webcam.

See this project wich will let you have fun with any webcam by creating a virtual webcam (with effect, overlays, etc...) :
[CENTER][http://webcamstudio.wiki.sourceforge.net/]("http://webcamstudio.wiki.sourceforge.net/") [/CENTER]

Good luck!

---

