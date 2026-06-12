---
title: "Increase Maximum Volume"
date: 2008-12-12
forum: Desktop Environments
---

### Post by Cook66 on 2008-12-12
Hey

I've got a Acer Aspire 6920 and recently installed Ubuntu. It didn't have support for my sound driver so after a lot of tinkering with things I don't really understand I managed to get it working.

The sound volume is way too low however. When I had Windows Vista installed I could get at the very least 500% more out of my speakers. Now with everything cranked up to max I can barley hear anything.

I wonder if there are any hidden volume control somewhere that I've missed or if it is possible for me to increase the maximum volume.

I primarily need to make things louder for playing media, but the low sound volume goes for everything on my desktop.

---

### Post by jalirious on 2008-12-26
try (in command line)
alsamixer

---

### Post by albinootje on 2008-12-26
> **Cook66 said:**
> 
I primarily need to make things louder for playing media, but the low sound volume goes for everything on my desktop.

I've seen the same problem on at least one other laptop (a Fujitsu Siemens), and I'd also like to know a solution for this.

---

### Post by broken tibula on 2008-12-26
Yeah, I'd be interested in a solution as well.  I looked a little while ago but didn't find anything--the only answer I found was to put on headphones, which does make it louder, but it doesn't help if my friend and I want to watch a movie.

**jalirious**, I tried alsamixer, but it's already set to 100.  Thanks, though.

---

### Post by Chibana on 2008-12-26
I actually have the same problem on my PC.  I was running 8.04.  I did a wipe and reinstall to 8.10, and now my sound is very quiet.  The hardware is the same.  I was able to use alsamixer on 8.04 to get the volume up, but now it shows it maxed out (100), but it's very quiet.  I have to turn the volume up to almost max on the speaker system to hear videos, etc., and if I don't put it back when switching the KVM (which includes sound) back to my XP box, it's deafeningly loud.

---

### Post by gogitosbanditos on 2009-02-17
The same with configuration 'Acer Extensa 5220 + Ubuntu 8.10'
It bores. I already have an installed alsamixer, but still nothing happens.

I am musician, it is very important thing for me :)

---

### Post by gus.ke on 2009-05-21
Have you tried using the volume control application (right-click on the volume icon in the toolbar and select "Open Volume Control")? You can use it to boost the speaker volume in relation to the master volume control (the one you see in the utility bar)  I got about 25% more volume by putting all the sliders on max.

---

### Post by cwbar_1 on 2009-05-21
I know that this is not the solution you are asking for but,,,,, Same problem vanished when I switched to Kubuntu! (HP Pavilion DV6000)

---

### Post by freakalad on 2009-05-22
alsamixer -c 0

---

### Post by argail1980 on 2009-07-01
often this is a problem of a misconfigured ALSA. For many Laptos you have to add a line to ```
/etc/modprobe.d/alsa-base.conf
```

In my case (LG Laptop P1 pro), I have a hda-intel based card. I had to add the line 

```
options snd-hda-intel model=lg
```

at the bottom of the file

```
lspci
```

should tell you what card you have.

then look in

```
/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
```

what the appropriate line is to add to the config file

---

