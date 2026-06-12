---
title: "Loading ubuntu from a memory device."
date: 2005-12-31
forum: General Help
---

### Post by floyd27 on 2005-12-31
Hey..
I a thinking of getting a memory module to load linux from.  1 gig one should be enough for a min install.
My question is should i be looking at compact flash cards or USB sticks?
Mainly which would make a better choice for loading a linux OS. Speed and complexity wise.. I am in the initial stages of trying this out. I have been using ubuntu for a year now and want to see if i can learn something more complex. I have a feeling I will learn a ton about the kernel itself etc.. And cant wait.. 

Anyone wanting to show me down the right path is welcome to do so..
thanx..

---

### Post by briancurtin on 2006-01-01
i have no idea about compact flash, but i would look at this page on the wiki about installing from a USB memory stick. it details what needs to be done in order to have this work correctly. [https://wiki.ubuntu.com/Installation/FromUSBStick?highlight=%28install%29%7C%28USB%29](https://wiki.ubuntu.com/Installation/FromUSBStick?highlight=%28install%29%7C%28USB%29)

a 1 GB stick should be good for everything, since the full install runs on a regular CD and is like a little over 600 MB or something

---

### Post by floyd27 on 2006-01-01
Does anyone know of an approx. increase in performance i should expect at boot?
I was reading and usb sticks are usually 5mb/sec data transfer rate..
SATA is 150mb/sec but i dont know if it means the same thing?

---

### Post by Swab on 2006-01-01
You will see a huge decrease in performance... flash memory is extremely slow compared to hard drives... also 1GB is not enough for a full install.

---

### Post by floyd27 on 2006-01-01
hmmm.
So if its so much slower why would people do it?
I was thinking it would be a significant improvment in performance..

---

### Post by sciurus on 2006-01-02
[QUOTE=floyd27]So if its so much slower why would people do it?[/QUOTE]

Portability.

---

### Post by briancurtin on 2006-01-02
[QUOTE=Swab]You will see a huge decrease in performance... flash memory is extremely slow compared to hard drives... also 1GB is not enough for a full install.[/QUOTE]
i read this thread incorrectly. 1 GB is good enough to install from the memory device, but i didnt realize he was trying to run from the memory device, where 1 GB wouldnt be enough. i kind of thought he worded it incorrectly in the title, but it ended up being me reading it incorrectly.

---

### Post by floyd27 on 2006-01-02
Sorry about that..
I was trying to use a flashcard or usb stick to load the linux OS from. Then use my HDD to store all my files..
I thought it would increase performance and make it boot almost instantly? 
Iv seen a system built that had 4 dual core opterons and a array of hard drives. (it was in a magazine.) They used a compact flash card to boot the linux OS. 
This system was a no expense spared kind of built. Where there was those thermaltake liquid cooling towers cooling each CPU. 
I though if they used flash cards to boot from it must be good......
Also they had hard wired the flash card to a spliced USb cable to attach it permantely. So potability was not a issue there...

---

### Post by Swab on 2006-01-02
You can buy a compact flash to IDE adapter for next to nothing.  I'm using one in my mini ITX with a 1GB compact flash... but it's slow as hell so I'm planning on replacing it with a microdrive.

---

