---
title: "Install Quake3PC on Ubuntu?"
date: 2006-08-17
forum: Gaming &amp; Leisure
---

### Post by Mike_N on 2006-08-17
I was told that my PC version of Quake 3 can be installed on Ubuntu through some "universal binary" file or something or the other? Can anyone explain this process to me?

Thanks, Mike

---

### Post by jonifen on 2006-08-17
Hi Mike,

I managed to install Q3 on my machine by downloading the Q3 point release 1.32b from [ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3apoint-1.32b-3.x86.run](ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3apoint-1.32b-3.x86.run) and then doing a

sudo sh linuxq3apoint-1.32b-3.x86.run

I deselected the Quake III Team Arena and Dedicated Server options as I dont use either of them (I think you do need the Q3TA cd for the Team Arena option though).

When it has finished installing, I copy the PAK0.PK3 from the Quake 3 CDROM to the installation directory by doing a

sudo cp /media/cdrom/Quake3/baseq3/PAK0.PK3 /usr/local/games/quake3/baseq3

When that completed, its good to go. For reference, your configs and the like are in ~/.q3a/baseq3 (or arena for RA3 / threewave for Threewave CTF).

Hope that helps!

If you choose to play online, you will need Punkbuster updated. I use PBSetup from [http://www.evenbalance.com](http://www.evenbalance.com) to keep it updated, as its quicker updating there than on a server.

---

### Post by DarkAngel88 on 2006-09-19
Thanks for this post jonifen, now I can play q3 on my laptop !!

Only a couple of issues... I don't have any sound !!  This is the output in the console : 

```
------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------
Sound memory manager started

```

Also, I always have the error about the fact that I cannot write to q3config.cfg.  I tried to set the permissions to write (755) to the file AND the directory where the pak files are located without any success.

Also, from times to times, the game just simply crash without any warning.  This is what I get in the console : 

```
quake3.x86: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Received signal 6, exiting...
Shutdown tty console

```

Any ideas will be greatly appreciated !

---

### Post by captainwitherspoon on 2007-07-29
I believe the "signal 6" error is caused by punkbuster, I'm having the same problem. I'd really like to fix this, any ideas anyone?

---

### Post by MrHippocampus on 2007-07-29
You could try [ioquake3]("http://ioquake3.org/"), its been reworked so openAL is used for sound which should hopefully fix your sound problem, not sure about the other one though :(

---

### Post by spy109 on 2007-08-10
I am having the same punkbuster problem.   Any help would be great cause this is super annoying and I know I can not be the only one out there.

---

### Post by arch stanton on 2007-08-10
nope you aren't alone ..got punked by punkbuster too

---

### Post by spy109 on 2007-08-11
I put a ticket in to Even Balance but had no luck as of yet.  And its probably been almost a month.   They seem to respond slow.

---

### Post by K.Mandla on 2007-08-11
I'm moving this over to Gaming and Leisure; it might get more attention there from people who have experienced this problem. ;)

---

