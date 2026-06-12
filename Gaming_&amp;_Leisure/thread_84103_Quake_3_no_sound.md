---
title: "Quake 3 no sound"
date: 2005-10-30
forum: Gaming &amp; Leisure
---

### Post by MarkUK on 2005-10-30
Seems more troubles 

Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp


Seems its protected tried running it in root sudo quake3 but its still the same

---

### Post by Dr. Falken on 2005-11-01
Add these lines to the quake3 script, before the "./quake3.x86 $*" line

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss


I have sound... but the game crash.

---

### Post by pmjdebruijn on 2005-11-21
Or, try these binaries:
[http://www.xs4all.nl/~bruijn9/quake3/](http://www.xs4all.nl/~bruijn9/quake3/)

Good luck,
Pascal de Bruijn

---

### Post by Demosthenes on 2005-11-21
Thanks a lot, those binaries worked for me.

---

### Post by thak on 2005-11-22
[QUOTE=Demosthenes]Thanks a lot, those binaries worked for me.[/QUOTE]

They worked for me, too, kinda.

If I run from the command line, they work great.  If I create a launcher, sound still doesn't work...(And the entry in the Debian menu created by the Loki installer doesn't have sound, either.)

Any ideas?

---

### Post by sinbad782 on 2005-11-25
The new binaries have a different name for the main executable. It's usually 'linuxquake3' or similar. You'll have to use your menu editor to change the shortcuts to reflect this. 

I've got this working pretty well now. I was having sound issues with both ET and Quake 3 under KDE. 

PJS

---

### Post by th3t1nm4n on 2006-05-28
When I try the first method of "echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" (I added it to /etc/init.d/bootmisc.sh like in [http://ubuntuforums.org/showpost.php?p=967572&postcount=5]("http://ubuntuforums.org/showpost.php?p=967572&postcount=5")) I get sound, but the game crashes.

When I try the ioquake binaries it claims that I don't have punkbuster installed, and I can't figure out why. Any more ideas?

---

### Post by EPOX123 on 2006-06-28
Try to compile this program it got my m-audio audiophile 2496 to work.

[http://www.craknet.net/joss/](http://www.craknet.net/joss/)

I made a deb pack dont have a place to upload it.

---

### Post by crane on 2006-06-28
[QUOTE=th3t1nm4n]When I try the ioquake binaries it claims that I don't have punkbuster installed, and I can't figure out why. Any more ideas?[/QUOTE]

Found this on theier site.
> Even Balance's Punkbuster support can never
be included with any open-source version of Quake 3 due to it being removed from the
source-code before the release, and the binary-only nature of its anti-cheating software.

---

### Post by jonifen on 2006-06-29
You can force an update of punkbuster using PBSetup from [www.evenbalance.com](www.evenbalance.com) but you'll probably find that you'll have problems with using a third party quake3 binary to play the game.

---

### Post by Josh_b on 2006-08-18
> **pmjdebruijn said:**
> Or, try these binaries:
[http://www.xs4all.nl/~bruijn9/quake3/](http://www.xs4all.nl/~bruijn9/quake3/)

Good luck,
Pascal de Bruijn

Probably a stupid question, but how do I get the binaries to work?

---

### Post by MadMan2k on 2006-08-18
those binaries orginate from here:

[http://www.icculus.org/quake3/](http://www.icculus.org/quake3/)

---

### Post by Josh_b on 2006-08-22
but how do I run them?

---

### Post by th3t1nm4n on 2006-09-16
.run and .sh files are just shell scripts.
```
sudo sh ~/Desktop/xxx.sh
```

---

### Post by slyvren on 2006-10-09
I dont recommend doing that to fix sound if you play multiplayer.  PB wont' work and i think we should try to keep the community "official". 

You can get it running natively.  I had to edit ~/.q3a/baseq3/q3config.cfg  look for a line that says 'seta snddevice "/dev/dsp"'  I just had to change 'dsp' to 'dsp1' your results may vary, but I'd recommend trying dsp0, dsp1, adsp, adsp1, adsp0, dsp2 .. etc.

---

### Post by DragonTU84 on 2007-02-02
Agree with Slyrven

This worked for me for id's version: quake3 1.32b

open the file ..
~/.q3a/baseq3/q3config.cfg

edit the line:
seta snddevice "/dev/dsp"

to:
seta snddevice "/dev/dsp1"

I changed the /dev/dsp to /dev/dsp1, and it worked for me (on Dapper).

---

### Post by Rhemat on 2010-07-03
Unfortually, using echo "quake3-smp 0 0 direct" > /proc/asound/card0/pcm0p/oss and it's accompanying command doesn't work for me, and I changed the config file to point to the proper dev device (both dsp and adsp are valid choices in my system).
I am using Linux Mint 9, KDE version, which I know isn't Ubuntu, but this distro is so close to Ubuntu that I can follow Ubuntu/Kubuntu guides and they work for this (sometimes).  Any ideas of what I could do?
Thanks in advance.

---

