---
title: "Fresh 7.10 install, no sound on Inspiron 1720"
date: 2008-02-28
forum: Dell  Ubuntu Support
---

### Post by obloxeon on 2008-02-28
I just put Ubuntu 7.10 on my Inspiron 1720 and I haven't been able to get the sound to work. I have tried all these methods:

1. sudo aptitude install linux-backports-modules-generic

2. alsa-driver-1.0.15 as well as alsa-driver-1.0.16

3. XFiDrv_Linux_US-1.04 which says I don't run a 64 bit OS, when I do (

4. sudo module-assistant auto-install alsa (the 4 line instructions)

5. Made sure my privileges were properly set for my user for audio enabled


Linux bishop-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
0e:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG (rev ff)

The top one is my onboard, the bottom one is my Creative Soundblaster X-Fi, which I hear doesn't work, but then there is the 64-bit drivers which are suppose to work (see #3), but they just say that I don't have a 64 bit OS.

I keep getting these errors:

"No volume control GStreamer plugins and/or devices found."

"gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing."

Someone, please help. I would love to get my X-FI card working since the sound is much better than onboard, but at this point, I would settle just to have some sort of sound. Any help would be greatly appreciated. Thanks in advance!

---

### Post by trmentry on 2008-02-29
Just curious.. .have you tried to install just 1 or the other sound card?  

Disable the onboard in bios and try the xfi.  

Or pull out the xfi and use just the onboard.  

Sounds like a conflict to me, but not totally sure.

I have a 1520 and just had to the backports thing to get on board audio to work.  From this **[post](http://ubuntuforums.org/showthread.php?t=577469)**.  But I'm sure you seen this one already.

```

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


```


Edit:  One thing to note... I'm running 32bit 7.10  as I couldn't get 64bit to install succesfully.

---

### Post by gonesolo on 2008-02-29
From expierence the X-Fi driver is a pain in the rear to install. Even on a 64 bit OS.

I had one but luckily I also had my old reliable Live 24 card, so I took out the X-Fi and installed the LIVE 24 instead.

---

### Post by groovete on 2008-02-29
Never got the sound work satisfactorily on my inspirion 1720 with Gutsy on it. Now I have Hardy Heron Alpha 5 installed. Sound (onboard) works great out of the box. Even the mic works like it should!!!
Ubuntu 8.04 LTS is scheduled for release in April 2008 ...
I think, it would be worth to wait.

---

### Post by CompleteMike on 2008-04-17
Hello,

I have been struggling with this audio issue for a couple of days.  I received suggestions here: [http://ubuntuforums.org/showthread.php?p=4736454#post4736454](http://ubuntuforums.org/showthread.php?p=4736454#post4736454) which involved this: [http://85.17.184.130/forums/index.php?showtopic=30750](http://85.17.184.130/forums/index.php?showtopic=30750)

This worked for me.  Specifically, I did this part from that page:

1. System-> Administration-> Synaptic Package Manager
2. settings at the top -> repositories -> updates -> tick gutsy backports close and reload as before.
3. Close Synaptic package manager then open a terminal,
4. sudo apt-get install linux-backports-modules-generic
Backports uses alsa 1.0.15rc3
then 
5. reboot
6. open a terminal and type
7. alsamixer
8. you should have sound

It worked for me on a Dell 1720 Ubuntu 7.10 install

Mike

---

