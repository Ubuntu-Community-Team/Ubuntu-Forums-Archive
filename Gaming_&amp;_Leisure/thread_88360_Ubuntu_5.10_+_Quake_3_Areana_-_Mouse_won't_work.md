---
title: "Ubuntu 5.10 + Quake 3 Areana - Mouse won't work"
date: 2005-11-10
forum: Gaming &amp; Leisure
---

### Post by vamsee on 2005-11-10
Hello,
I've made a switch to Ubuntu 5.10 yeserday night - after 4 years of RH/Fedora. 
My problem is, Quake 3 won't have sounds and mouse won't move. I solved the "cannot mmap /dev/dsp" problem with these two lines:

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

The mouse still doesn't work. I've installed nvidia drivers with apt-get install nvidia--glx.

Any ideas how to make my mouse work?

Regards,
Vamsee

---

### Post by Miguel on 2005-11-10
Hi vamsee

try killing esd before running quake 3. I do it this way for running racer, so it might help. Just type in a terminal

$ killall esd

To run it again, type from a terminal

$ esd -nobeeps &

As you have put esd on the background, you can safely close that terminal

Hope it helps

---

### Post by slux on 2005-11-10
You might also want to check out [http://icculus.org/quake3/]("http://icculus.org/quake3/") for q3 with full featured alsa support. I guess pb won't work with source modifications. Is that a problem for q3 online play currently?

---

### Post by vamsee on 2005-11-10
[QUOTE=Miguel]Hi vamsee

try killing esd before running quake 3. I do it this way for running racer, so it might help. Just type in a terminal

$ killall esd

To run it again, type from a terminal

$ esd -nobeeps &

As you have put esd on the background, you can safely close that terminal

Hope it helps[/QUOTE]

My problem now isn't the sound. Sounds working fine. But the mouse is struck - the buttons work but the cursor won't move. :(

---

### Post by Miguel on 2005-11-10
Sorry Vamsee, I can't help you with the last one. Maybe someone more knowledgeable jums in.

---

### Post by GIBson3 on 2005-11-10
[QUOTE=slux]You might also want to check out [http://icculus.org/quake3/]("http://icculus.org/quake3/") for q3 with full featured alsa support. I guess pb won't work with source modifications. Is that a problem for q3 online play currently?[/QUOTE]

in theory, Online play is still available, however you are unable to play on a punkBuster enabled server.  I'm not sure it Pure server maters or not (SV_PURE 1)

As for the Mouse issue, what mouse driver are you using?

---

### Post by vamsee on 2005-11-11
[QUOTE=GIBson3]in theory, Online play is still available, however you are unable to play on a punkBuster enabled server.  I'm not sure it Pure server maters or not (SV_PURE 1)

As for the Mouse issue, what mouse driver are you using?[/QUOTE]

Microsoft Optical mouse (2 button + wheel) but on PS/2, not USB.

---

### Post by slux on 2005-11-11
[QUOTE=GIBson3]in theory, Online play is still available, however you are unable to play on a punkBuster enabled server.  I'm not sure it Pure server maters or not (SV_PURE 1)

As for the Mouse issue, what mouse driver are you using?[/QUOTE]

Yeah, but what I was really asking was whether or not punkbuster is currently widely enabled for Q3 servers now that the source is out?

icculus.org version also uses SDL for input which might help with the mouse although I'm sure there's a way to make the original work as well. :P

---

### Post by GIBson3 on 2005-11-11
[QUOTE=slux]Yeah, but what I was really asking was whether or not punkbuster is currently widely enabled for Q3 servers now that the source is out?

icculus.org version also uses SDL for input which might help with the mouse although I'm sure there's a way to make the original work as well. :P[/QUOTE]

There still seems to be a fair number of PB enabled's...

as for the Mouse, that is very strange, could you post a copy of the Q3A Console output?

also maybe your xorg.conf

---

### Post by vagnihotri on 2008-12-19
Hi,

Thanks for the sound issue :)
I was able to solve mouse issue after lot of searching.
But I found key for it in README-linux.txt of quake3, not the solution but I derived solution from it.

on quake3 startup, I saw a line as "XF86DGA Mouse (Version 2.0) initialized".

I read README-linux.txt and it says:
By default, Q3A Demo will attempt to use DGA mouse handling. DGA
support features direct reading of the mouse motion and provides
more accurate control while playing the game. By default this
support is enabled, but can be disabled by adding
"+set in_dgamouse 0" to the command line at startup. This is recommended if you are using a Voodoo3 and are experiencing black screens, lockups,
or mapping of mouse input to key events. This bug should be
resolved on XFree86 SVGA 3.3.5 (except for a blue mouse cursor
you might notice on the initial fullscreen frame). DGA mouse
support does not require root privilege.

So simple fix was disabling it, and activate mouse with following:
./quake3  "+set in_dgamouse 0"


--Vinit.

---

