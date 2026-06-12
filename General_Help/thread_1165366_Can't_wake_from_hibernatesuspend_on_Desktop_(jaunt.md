---
title: "Can't wake from hibernate/suspend on Desktop (jaunty 9.04)"
date: 2009-05-20
forum: General Help
---

### Post by ihaveabu on 2009-05-20
I'm running a computer i built a few years ago. here's the specs:
P4 2.4c
Asus P4P800 Mobo
ATI Radeon 9600
2GB DDR2 PC3200
120GB HDD (seagate or WD)
Wireless mouse and keyboard
 
I can enter suspend and hibernate just fine. I just can't seem to wake from it. Pressing buttons on the keyboard, moving the mouse, pressing the power button. nothing works. I have to press the hard reset button each time to get my computer to restart. 
 
I understand suspend/hibernate has a lot of problems with linux. But I'm not running any kind of special drivers or anything. I haven't installed a single driver since I installed Jaunty, and apparently I don't need to since my video card just uses the legacy video card drivers that comes with jaunty.
 
help?

---

### Post by ihaveabu on 2009-05-21
anyone?

---

### Post by ihaveabu on 2009-05-23
help?

---

### Post by KhurramM on 2009-05-23
On grub there is recovery mode.

Just use it.

I hope your current boot issue will be resolved automatically.

On linux hibernate/suspend is not good if it causes such issues. Try avoiding it.

May be future kernels have a solution to this.):P

---

### Post by ihaveabu on 2009-05-23
i can't use grub if pressing the power button doesn't do anything. right now, when i suspend/hibernate, the screen turns off, but the computer's fans are still on. pressing the power button doesn't do anything. how do i use grub?

---

### Post by ihaveabu on 2009-05-26
i'm pretty sure there's a lot of people with this problem. any luck anyone?

---

### Post by kevin82485 on 2009-05-29
I'm having pretty much the exact same issue.  I enter suspend mode and my screen goes black with the exception of a white cursor in the top left of my screen.  All the fans in my computer are still running, and it is completely unresponsive.  The only way to "wakeup" my computer is to hard reset it.

I have a computer I built myself.  Dual boots Ubuntu 9.04 or Win XP.  ASUS P5B Deluxe, Intel Core 2 Duo E6600, 3 GB RAM, Nvidia GeForce 9800 GT.

The only driver I installed was the recommended driver for my video card.

If anyone know how to fix it please PM me.

---

### Post by ripiajo on 2009-06-07
Same issue here. I have 1gb ram and about 1gb swap partition (not sure now exactly how many bytes). I just read that ubuntu hybernates to the swap partition. Could this be part of the problem? If my swap parition contains some data, the ram+swap contents would not fit in the swap partition, and I see no way that the computer can restore its previous state after hybernation.

What is the size of your swap?

---

### Post by DouglasAWh on 2009-06-30
What's a reasonable swap size?  I've got 2.33 GB here and have the same problem.

EDIT: increased swap to 6.08 GB and still have the issue.  I'm going to try updating the BIOS on this HP nc6230.

---

### Post by Pollywoggy on 2009-06-30
> **ripiajo said:**
> Same issue here. I have 1gb ram and about 1gb swap partition (not sure now exactly how many bytes). I just read that ubuntu hybernates to the swap partition. Could this be part of the problem? If my swap parition contains some data, the ram+swap contents would not fit in the swap partition, and I see no way that the computer can restore its previous state after hybernation.

What is the size of your swap?

I have an HP Mini-Note (2133) and I have 1GB or less of swap and I do not have this problem.  Both hibernate and suspend work.  Is there a way to quickly check how much swap I have?

---

### Post by DouglasAWh on 2009-07-01
I think it may be an issue with the kernel.  Fedora 11 works on the same hardware for me.  I'm going to test Karmic Alpha 2, but I'm going to have to wait a while for the download to finish. :(

UPDATE: Karmic did not work.

---

### Post by chngr on 2009-07-02
I am having the same issue with suspend and hibernate. My Comp suspends and hibernates, screens turns off fans turns off but can't resume from both. Any of the buttons on my computer can't work.
By the way Pollywoggy type
```
free -m
```
you see your swap partition size in Mb.

---

### Post by FMJammo on 2009-07-04
I am having the same issue here, i am still running 8.10 because of AMD are slow to release new drivers for my video card. My computer refuses to wake from hibernate. I have seen few ways to recover it: 1- hard reset, 2- access from remote computer with remote desktop. I don't know why my computer goes to hibernate mode, i set it to never go to hibernate.

---

### Post by A_M_S on 2009-07-06
Same problem here!

Suspend Works fine but i can't recover from hibernate :(

I have a ASUS laptop with a AJ6J MB and a core duo from Intel (T2250@ 1.73GHz).

---

### Post by starcraftmaster on 2009-07-06
same problem too
i cant hibernate at all
it just freezes and i have to hard reset

---

### Post by FMJammo on 2009-07-06
I fixed blank screen by disabling screensaver and hibernate. I simply set to turn off screen after sometimes.

---

