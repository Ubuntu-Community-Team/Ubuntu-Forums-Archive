---
title: "Abit ol' WoW trouble"
date: 2006-08-09
forum: Gaming &amp; Leisure
---

### Post by kimusabi on 2006-08-09
Hi.
I'm having abit of trouble with World of Warcraft. Not only does it lag on the login screen ( a graphic problem I think), but I'm not getting any sound.

Edit: Everytime I run winecfg and select the audio tab, I get returned with this error.
```
kimusabi@cyberdrain:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/kimusabi/.kde/socket-cyberdrain.
can't create mcop directory
kimusabi@cyberdrain:~$

```

Suggestion's?

Cheers
-Kimmeh

---

### Post by snowpalmer on 2006-08-09
> **kimusabi said:**
> Hi.
Everytime I run winecfg and select the audio tab, I get returned with this error.
```
kimusabi@cyberdrain:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/kimusabi/.kde/socket-cyberdrain.
can't create mcop directory
kimusabi@cyberdrain:~$

```

Check [this link]("http://www.linuxquestions.org/questions/showthread.php?t=394282") out and see if it helps.  I've had this in the past and it seems like I either had to create the .kde directory or set permissions on it. Later in that post they say to get the latest version of arts which may or may not be your problem. 

Although I wish I could get WoW to work on my machine ](*,)

---

### Post by kimusabi on 2006-08-09
I managed to fix the sound problem by switching from my nVidia nForce2 (ALSA Mixer) to Realtek ALC650F (OSS Mixer). Work's wonder's now.

Then again. There is still the problem of the real low frame rate.
Anyone else have this problem, and does anyone else have any solution's?

Also, thank's snowpalmer for the link. But it didn't really help me. Sorry :-( 

Cheer's for you're time.
-Kimmeh

---

### Post by kimusabi on 2006-08-09
Bump?

---

### Post by simplyw00x on 2006-08-10
Do you have 3D drivers for your grpahics card installed?
Are you running using D3D or OpenGL?
What specs are your machine?
How did you install WoW?

---

### Post by kimusabi on 2006-08-10
1. Yes I do have the nVidia driver's installed
2. Honestly no idea
3. AMD Sempron, nVidia GeForce4 MX Integrated GPU, 512MB RAM (this is all off the top of my head, so it might not be all right).
4. I followed the guide on the Wine application database [ Link here.](http://appdb.winehq.org/appview.php?iAppId=1922)

---

### Post by simplyw00x on 2006-08-10
My best suggestion is to install the version of wine from
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
and then make the appropriate Config.WTF changes as listed there. If you made no such changes to the default install, you'll be using D3D mode which is buggy and slow.

---

### Post by kimusabi on 2006-08-10
Just added the three line's from that guide into the Config.WTF and it seem's to work fine for the moment.

Cheer's
-Kimmeh

---

