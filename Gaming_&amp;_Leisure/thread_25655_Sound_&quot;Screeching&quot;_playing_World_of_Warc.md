---
title: "Sound &quot;Screeching&quot; playing World of Warcraft in Cedega in a 32bit chroot on Hoary64"
date: 2005-04-10
forum: Gaming &amp; Leisure
---

### Post by FrankBob on 2005-04-10
Hi, I'm not sure if this is a AMD64 specific problem or not so I'll just post it here.

I've set a 32bit chroot in Hoary64 following instructions in [http://www.ubuntuforums.org/showthread.php?t=24575](http://www.ubuntuforums.org/showthread.php?t=24575)

I have cedega 4.3-1 running in the chroot and it can run World of Warcraft which I've just copied over from my ntfs partition. The graphics work great and I have nvidia-glx installed in the chroot.

Sound is inconsistent however. The music usually plays well in the login screen but in game (and sometimes before it loads) the sound switches to a very lound screeching noise. The screeching starts and stop randomly. 

I think cedega defaults to using OSS for sound output. I can edit the cedega configuration to use alsa instead in which case there is no sound at all. I have no idea where the problems lies especially since sometimes it works but not consistently. 

I dont know if this is related but it might explain why alsa doesn't work at all: If I go in System->Preferences->Multimedia Systems Selector. For default sink, ESD and OSS work, but ALSA gives me a "Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture" error. So alsa dosen't seem to work at all (64 bit part, at least).

I also only have a dim understanding on how sound works at all in linux. How does sound make its way from the 32bit chroot to my speakers? Can the problem be outside the 32bit chroot?

I have integrated AC'97 sound on my Via motherboard:

Via K8MM-ILSR
VIA® K8M800 Chipset
6 Channel software audio codec Realtek ALC655

Any ideas or similar problems?

Oh I have also played Warcraft3 and have not had the same problem. sound seems to work well there.

Frank

---

### Post by FrankBob on 2005-04-10
After a bit more looking around a the TransGaming forums, I found someone who had a similar problem.

Some other guy:

> I've installed WoW and randomly the sound will go very loud and staticy and then randomly it will switch back to perfect sound. I was wondering if there is an easy way to fix this.

I'm using the latest Ubuntu (Hoary) with Cedega 4.3. I've got an onboard AC'97 for sound. I'm not sure why it'd be needed but I'm on using an AMD XP 2000+, GeForce FX 5600 ultra and 768MB of RAM. I'm playing WoW using opengl.

Alright, I figured out the problem. Just in case anyone else has issues I'll post the solution. In your config file for cedega (which is in home/USERNAME/.transgaming/ ) change the value of

"Drivers" = "wineoss.drv"

to

"Drivers" = "winealsa.drv"



So according to him, using alsa should fix the problem but my alsa doesn't work!

I don't know how to make it work.

Frank

---

### Post by Giawa on 2005-04-11
Wooooaw. That was me that posted in transgaming. Small world ;-) Yup, switching the drivers to alsa should work for you, as I had the same problem and it's fixed now :razz:

--Oops, just read the rest of your post. Guess I should read before posting. If ALSA doesn't start up Cedega should start up its own version of Directsound, which, although slower, should work as well. So, it's weird that no sound is coming thru when you switch to alsa. Make sure it's set properly.

Make sure you have the newest alsa-base from Synaptic. If it helps I also have alsa-utils, libpt-plugins-alsa and libwine-alsa, although I'm not sure which are needed for Cedega and if there are more, I just ran a quick search of alsa in Synaptic. Maybe also try a fresh install of alsa-base, just in case there is a problem there.

In your case, with an AMD64, it's kind of foreign territory to me, so I'm so sure what else to recommend. Good luck in solving your problem. I'll also try and see if I can find anything else that I might have done, but I think getting alsa to work is the major thing, as we both have the same integrated sound chips and version of linux, so... just got to get it working  :smile: Keep us posted!

--Edit: Try deleting you config.wtf file in the World\ of\ warcraft/WTF directory. This will get WoW to try and reconfigure for your system and might pick up a problem? This more helped me with frame rates though, not sound. But it's something to try.

--Edit2: After trying your Multimedia Selector under the System>Preferences Menu I found that my computer too gave me that error. Yet WoW still works with ALSA... weird.... Time to fool around with Cedega.

---

### Post by Giawa on 2005-04-11
Thought I'd make a new reply to stop with the edits. Okay, so my ALSA doesn't work either, haha. Odd... but my sound works fine and this is why. Cedega outputs this when I run WoW from terminal (I've always used a link before, so I never saw this).

This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.

So there's our problem, the AC'97 isn't capable I guess, oh well. So, my Cedega switches to DirectSound which seems to work just fine. Check to see what Cedega does from the terminal and post any errors it generates. I'm off to sleep for now, good luck.

---

### Post by FrankBob on 2005-04-11
Ok, after a quick search on the Ubuntu Bugzilla, I found two bug postings that seem very relevant. It seems that alsa doesnt work with my specific sound driver via-82xx out of the box. Some fixes are provided here

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6303](https://bugzilla.ubuntu.com/show_bug.cgi?id=6303)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8529](https://bugzilla.ubuntu.com/show_bug.cgi?id=8529)

I'll try them tonight. Bottom line is that this is probably a via-82xx specific problem.

Hope this works out.

Frank

---

### Post by FrankBob on 2005-04-12
I fixed the problem. I tried to use the Hoary i386 Live cd to run the game and it worked in alsa.  So the problem is probably due to some bug in the 64 bit version of the alsa driver.

The permanent solution however was simply to upgrade to the latest alsa driver compiled from source. alsa STILL doesn't work in Hoary 64 for WoW but now I can use OSS for WoW and there is no screeching. 

Frank

---

