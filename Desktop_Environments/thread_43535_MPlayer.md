---
title: "MPlayer"
date: 2005-06-22
forum: Desktop Environments
---

### Post by Prudentissimus on 2005-06-22
Hello,


  My situation: When I play a movie file (*.avi, *.vcd, *.vob) on FULL SCREEN, or Double size... or any size bigger than NORMAL,... the movie becomes increasingly choppy... Why is that

and how do i fix it.

---

### Post by Wombley on 2005-06-22
[QUOTE=Prudentissimus]Hello,


  My situation: When I play a movie file (*.avi, *.vcd, *.vob) on FULL SCREEN, or Double size... or any size bigger than NORMAL,... the movie becomes increasingly choppy... Why is that

and how do i fix it.[/QUOTE]

One thing you might like to try is running with the option -vo xv - this uses hardware acceleration to play the video.

---

### Post by Prudentissimus on 2005-06-22
[QUOTE=Wombley]One thing you might like to try is running with the option -vo xv - this uses hardware acceleration to play the video.[/QUOTE]
 is there a thing I can do to allow hd acceleration on all apps i run?

---

### Post by Bandit on 2005-06-22
[QUOTE=Prudentissimus]is there a thing I can do to allow hd acceleration on all apps i run?[/QUOTE]

What is your hardware specs?

---

### Post by Prudentissimus on 2005-06-22
[QUOTE=Bandit]What is your hardware specs?[/QUOTE]
 Thermaltake Xaser III VM3000 Blac 
480W - Thermaltake W0020RUC Purepower 
Asus A7N8X-E Deluxe nForce2 Audio/LAN/USB 
AMD Athlon XP 3200+ (Barton) 400 FSB 512K @ 426FSB ~= 2.343 Ghz.
DDR (400) 3200 - 512 MB (2 pcs 256) Corsair
IDE - Western Digital (WD1200JB SE) 120 G 
IDE - Western Digital (WD1200JB SE) 120 G
DVD-ROM - Lite On XJ-HD166S 16x DVD
Mitsumi 1.44 MB 3.5" Floppy Drive 
Audigy 2 Original
Asus GeForce FX 5700 256MB DDR/8X-AGP/TV- 425/500 @ 460/590
Windows 2000 Professional SP4

---

### Post by Bandit on 2005-06-22
[QUOTE=Prudentissimus]Thermaltake Xaser III VM3000 Blac 
480W - Thermaltake W0020RUC Purepower 
Asus A7N8X-E Deluxe nForce2 Audio/LAN/USB 
AMD Athlon XP 3200+ (Barton) 400 FSB 512K @ 426FSB ~= 2.343 Ghz.
DDR (400) 3200 - 512 MB (2 pcs 256) Corsair
IDE - Western Digital (WD1200JB SE) 120 G 
IDE - Western Digital (WD1200JB SE) 120 G
DVD-ROM - Lite On XJ-HD166S 16x DVD
Mitsumi 1.44 MB 3.5" Floppy Drive 
Audigy 2 Original
Asus GeForce FX 5700 256MB DDR/8X-AGP/TV- 425/500 @ 460/590
Windows 2000 Professional SP4[/QUOTE]

Well heck, mine doesnt skip and yours shure as heck shouldnt....
Using the -ao xv didnt fix it???
Just out of curiosity what does your CPU load show while running it?
This may not apply to Ubuntu, but on SuSE we had a few problems like this with peoples (AMD64) CPUs doing this due to stepping.  Have you tried turning power management off? I think there is more to it. What was happening was the CPU slowing its self down to save power and it was not very responsive about boosting its self back up to full speed. Making some things lag. Most time you could not tell the diference cuz Linux not needing much resorces at all.

Cheers,
Joey

---

### Post by Prudentissimus on 2005-06-22
[QUOTE=Bandit]Well heck, mine doesnt skip and yours shure as heck shouldnt....
Using the -ao xv didnt fix it???
Just out of curiosity what does your CPU load show while running it?
This may not apply to Ubuntu, but on SuSE we had a few problems like this with peoples (AMD64) CPUs doing this due to stepping.  Have you tried turning power management off? I think there is more to it. What was happening was the CPU slowing its self down to save power and it was not very responsive about boosting its self back up to full speed. Making some things lag. Most time you could not tell the diference cuz Linux not needing much resorces at all.

Cheers,
Joey[/QUOTE]
 my CPU is almost always 0%...

Maybe 10% when running games or something.

---

### Post by Bandit on 2005-06-22
[QUOTE=Prudentissimus]my CPU is almost always 0%...

Maybe 10% when running games or something.[/QUOTE]

Thats good, shows there isnt a stepping issue.
Lets see..
UDMA on the drive is "ON" correct?
Does it skip ahead on the video or is there a delay in the skips?
This can determin is the drive is going to fast or to slow.
Let me know.
Cheers,
Joey

---

### Post by Prudentissimus on 2005-06-22
[QUOTE=Bandit]Thats good, shows there isnt a stepping issue.
Lets see..
UDMA on the drive is "ON" correct?
Does it skip ahead on the video or is there a delay in the skips?
This can determin is the drive is going to fast or to slow.
Let me know.
Cheers,
Joey[/QUOTE]
 Well, I attempted to play an xViD / Divx AVI file...

The sound is faster than the Video... a little bit, because I can hear the guy talk when his mouth was not moving at all...

and this AVI runs fine in Windows.

And when it runs in full screen or double size it just slows down... very slow.

---

### Post by Bandit on 2005-06-22
[QUOTE=Prudentissimus]Well, I attempted to play an xViD / Divx AVI file...

The sound is faster than the Video... a little bit, because I can hear the guy talk when his mouth was not moving at all...

and this AVI runs fine in Windows.

And when it runs in full screen or double size it just slows down... very slow.[/QUOTE]
 Well, I have had videos do that when a DivX files was played off a DVD disc (when using windows) the problem was that not enough data is being feed to the system from the DVD drive. 
Some where that drive is being bottle necked.
Dbl check the DMA settings on it. And also see if you can UN-SET the max speed on the drive so it spins faster.
Those are the only things I can think of.
Also when using the MPlayer, Did you compile it your self???
Or did you install it via a DEB package?
Cheers,
Joey

---

