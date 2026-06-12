---
title: "DVD plays at low framerate"
date: 2006-01-07
forum: General Help
---

### Post by fast orange on 2006-01-07
I moved from windows to a dual boot system with ubuntu on my laptop about a month ago...so I'm new to linux.  Windows is just a small partition for gaming...and dvd's

I can't find a player that will play dvd's at a good quality.  I didn't like the setup of mplyer and xine...and both weren't working that well for me.

VLC media player will play a DVD on my laptop, but the quality is poor.  Something is happening with the frames, the movie seems to skip around a little as I'm watching it...it is bearable, but much less pleasant than running winDVD in windows.  My computer has a 64mb mobility radeon video card, 512mb ram, 2.4gz pentium 4.

Has anyone had a similar problem with DVD playback.  Could i get relatively simple directions to fix this (I'm not completely familiar to linux yet).

---

### Post by Jens Willem on 2006-01-07
I've been using Ubuntu for several months, so I'm not an expert, but I experienced similar problems and solved them by enabling DMA. Perhaps this link can help you:

[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by fast orange on 2006-01-07
this didn't seem to do it, though i appreciate the help.  are there other possibilities.  are there adjustments to be made in VLC itself, or is this a DVD drive problem?

---

### Post by kes on 2006-01-09
2fast orange: I'm a bit surprised that you didn't find xine-ui satisfying, because it has a very wide variety of options (in Advanced or Expert mode);
there you can easly chage the reading speed for the disks so there woun't be missing frames...<_<
The characteristics of your hardware are more than enough to watch DVDs without any problems (I have approximately the same configuration and not experiencing any inconvenience with DVDs at all).

What about totem player? Does it work?

---

### Post by fast orange on 2006-01-10
on second thought...it was a DMA problem.  running the command "hdparm -d1 /dev/cdrom" fixes my problem.  However at startup it goes back to not working.  I edited /etc/hdparm.conf  with:
#/dev/cdrom {
#          dma= on
#}

but this didn't seem to do it,  i must be missing a command, can anyone help?

---

### Post by fast orange on 2006-01-10
just a note... i did type it as "dma = on" (not "dma=on") but my problem still persists.  Why isn't DMA being turned on at startup?

---

### Post by jasay on 2006-01-10
Remove the '#' signs.  They turn the lines into comments so that they are ignored by the computer.  Comments are useful for reminding yourself what various bits of code do or of other options you might use in a given bit of code.

---

### Post by fast orange on 2006-01-11
that did it!  i had no idea the # were there for a particular reason.  i just eneterd the stuff in the same pattern i saw above what i was typing.  thanks.

---

