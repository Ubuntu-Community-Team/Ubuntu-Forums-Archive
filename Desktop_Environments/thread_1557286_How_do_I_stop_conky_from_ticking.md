---
title: "How do I stop conky from ticking?"
date: 2010-08-20
forum: Desktop Environments
---

### Post by Mr_VeRiTy on 2010-08-20
Hi, I just realized today that my conky is *ticking* I know it's conky 'cos if I turn conky off the ticking stops, and the ticks are in sync with conkys update interval. How do I get the ticking to stop?

EDIT: Actually I think the ticking is coming from my processor fan or something next to it (it's in a laptop) 'cos the sound doesn't stop if i plug earphones in or mute it. But it is conky causing it. If I put my ear on my laptop keyboard where the processor is I can hear the ticking louder.

I Think it's the same problem as [this thread]("http://ubuntuforums.org/showthread.php?t=1235190"), but it doesn't do it when I resize windows.

Also It didn't tick yesterday, but before I went to sleep last night I installed system updates, some of which were kernel updates, after that it started ticking.

---

### Post by David Andersson on 2010-08-20
Can you post your ~/.conkyrc file here, or do you know if it polls the harddisk, or both?

---

### Post by Mr_VeRiTy on 2010-08-20
> **David Andersson said:**
> Can you post your ~/.conkyrc file here, or do you know if it polls the harddisk, or both?
I don't know what polling the hard disk is so i'll attach the conkyrc. I edited it myself, but nothing to cause the ticking sound. Also the ticking doesn't sound like it comes from the drive, the drive is at the opposite side of the laptop from the processor.

---

### Post by David Andersson on 2010-08-22
Does it tick once a second? If you change "update_interval" in .conkyrc and restart conky, will the ticking change?

If you remove the two lines containing the command "fs_free", does that change the ticking? (Save a copy of .conkyrc named .conkyrc-my-original or .conkyrc-backup for easy restoring.)

> **Mr_VeRiTy said:**
> Also the ticking doesn't sound like it comes from the drive, the drive is at the opposite side of the laptop from the processor.

I had an old computer which made some sound during cpu load, and it was not the fan. It was strange, because cpu load is just a lot of small electrical currents. So it could be your cpu, but then you should have that sound when scrolling web pages, and other intermitent cpu loads.

---

### Post by Mr_VeRiTy on 2010-08-22
> **David Andersson said:**
> Does it tick once a second? If you change "update_interval" in .conkyrc and restart conky, will the ticking change?

If you remove the two lines containing the command "fs_free", does that change the ticking? (Save a copy of .conkyrc named .conkyrc-my-original or .conkyrc-backup for easy restoring.)



I had an old computer which made some sound during cpu load, and it was not the fan. It was strange, because cpu load is just a lot of small electrical currents. So it could be your cpu, but then you should have that sound when scrolling web pages, and other intermitent cpu loads.
I put my ear where the CPU is and scrolled, and very faintly there was sound when scrolling, but i can only hear it when my ear is closer to the CPU. Changing the update interval to 2 makes it tick every two seconds. And the CPU is only 9-10 months old, and was new when i bought it. But when I bought it I was using 32bit Ubuntu, recently I switched to 64bit, could that have anything to do with it. Also it still ticks when I comment out the parts concerning my hard drive.

---

### Post by David Andersson on 2010-08-26
So there *is* a metaphysical connection between mechanics and electronics! :)

Complicated stuff in the TEXT section use more cpu. My uses at about four times as much cpu, than a .conky with only a simple ${hr}. The /etc/conky/conky.conf lays somewhere inbetween. In my .conky, tcp_portmon commands seems to be the worst. Try find out what is heaviest in your .conky and remove them. (Or change the problem from a conky problem to a hardware problem.)

---

