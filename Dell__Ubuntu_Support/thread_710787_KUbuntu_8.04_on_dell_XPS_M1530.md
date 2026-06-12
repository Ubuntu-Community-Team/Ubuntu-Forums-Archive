---
title: "KUbuntu 8.04 on dell XPS M1530"
date: 2008-02-28
forum: Dell  Ubuntu Support
---

### Post by LK_gandalf_ on 2008-02-28
Hi all. Anyone has installed the 8.04 version of kubuntu on this laptop?
I have to do this because of some bug in the 7.10 kernel. the 8.04 works fine for the ethernet, video, and programs, but I have problems with the audio (doesn't work), and other hardware.
Any suggestions?
Thank you :)

---

### Post by Taleman on 2008-02-28
Well since 8.04 is still in development (alpha release I think) I imagine it would be difficult to get it working just right. Wouldn't it be easier to go back to an older version like Feisty or Edgy?

---

### Post by LK_gandalf_ on 2008-02-28
the problem is that the old kernel has problem (and the older too i think), with the ethernet and something like the dhcp. In fact, they are well recongnized but the connection doesn't work in any way.

Is there a procedure to understand what drivers the audio card needs?

---

### Post by Taleman on 2008-02-28
> **LK_gandalf_ said:**
> the problem is that the old kernel has problem (and the older too i think), with the ethernet and something like the dhcp. In fact, they are well recongnized but the connection doesn't work in any way.

Is there a procedure to understand what drivers the audio card needs?
what sound card are you using..... did you try editing:

sudo gedit /etc/modprobe.d/alsa-base

---

### Post by LK_gandalf_ on 2008-02-29
I have this audio card:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

which is a SIGMATEL STAC 92XX C-Major HD Audio

but i don't klnow how to eventually edit the config file :(

---

### Post by Taleman on 2008-02-29
> **LK_gandalf_ said:**
> I have this audio card:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

which is a SIGMATEL STAC 92XX C-Major HD Audio

but i don't klnow how to eventually edit the config file :(

Add 

> options snd-hda-intel model=auto

at the end of 

> /etc/modprobe.d/alsa-base

---

### Post by ChaosParser on 2008-02-29
This should be in the development forum, you'll likely have better luck looking there. :)

---

### Post by LK_gandalf_ on 2008-03-01
yes, maybe it's better. However, the solution of taleman works, now the audio is OK. Thank you :)

But  i have other problems with the windows, I'll open a specific topic in the hardy forum.
However, anybody has installed the 8,04 on this laptop or similar?

---

### Post by laurence91 on 2008-05-21
Hi i have this been running 8.04 on an M1530 for a couple of weeks.

For the audio i installed a sound mixer program from adept, it works ok now as i put a widget on the bottom bar to adjust volume.

---

