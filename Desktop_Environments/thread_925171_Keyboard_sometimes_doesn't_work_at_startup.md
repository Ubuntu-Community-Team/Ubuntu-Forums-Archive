---
title: "Keyboard sometimes doesn't work at startup"
date: 2008-09-20
forum: Desktop Environments
---

### Post by Raskua on 2008-09-20
I'm using a compaq FS7600 and when I turn on the computer the keyboard has a 10% chance of not working. Then I turn off the computer and wait 10 secs. Then I turn it back on and it works. 

So basically it just doesn't work 1/10th of the times I boot up.

It does this with all the round circle plug(purple circle plug thing, I'm not sure what it's called.) keyboards I own.

Should I purchase a usb keyboard to fix this problem? Or is there another solution?

---

### Post by Raskua on 2008-09-21
I still have this problem if anyone knows the solution.

---

### Post by linux5uper on 2008-09-21
Have you tried unplugging & plugging the keyboard itself, without restarting the computer?

And does this happen on a clean startup, or do you resume from suspend/hibernation?

---

### Post by Raskua on 2008-09-21
It doesn't do anything if I do that. The funny thing is the light for Numlock is on, but I can't turn it off or anything when it doesn't work. I just click the restart option and it works fine.

I never hibernate it.

---

### Post by linux5uper on 2008-09-21
I just asked because my USB keyboard doesn't work on my laptop after hibernation (no problem with suspend), and I thought it might be connected to that. From your description, you have a PS/2 keyboard, and I read in another thread that updating the BIOS firmware fixed the problem in one such case. I would ask an expert or consult the manufacturer's website before attempting this though.

---

### Post by Raskua on 2008-09-21
It's not that great of a problem. Like 1/10 times I turn on my computer it does that. Would a USB keyboard completely eliminate that. I don't have a working PS/2 or whatever mouse because it's broken. But I think that wouldn't work either if I did. My USB mouse works perfectly fine when the keyboard sometimes doesn't.

---

### Post by linux5uper on 2008-09-22
If I were you I would borrow/buy one and test it. You can't be sure it'll work if you don't know the source of the problem you have.

---

### Post by Raskua on 2008-09-22
I have Ubuntu on my laptop and it works fine.

The desktop that it is having the keyboard problems is a Compaq FS7600, I don't know if there are any issues with that model. If so let me know. :)

---

### Post by l0co on 2009-04-08
Did anybody solve this problem? It's very annoying to have a 50% chance of not working keyboard at each startup (in my case).

I discovered, that the keyboard must have the same numlock state at system start-up as it was in previous session. I work in home on laptop keyboard and in office on external keyboard. Usually in home I have numlock off and in office numlock on. There is 100% chance of turning on system properly with external keyboard, when:
 * I leave the numlock  turned off at booting when I work in office after home work (when numlock was off)
 * I turn ON the numlock in GRUB, when I continue work in the office (when numlock was ON)

Other presets results always with not working keyboard.

IMHO ubuntu tries on some boot level to restore last numlock state and it doesn't work properly with USB keyboard connected to laptop. Does anybody have an idea how to turn this s...t off?

---

### Post by mbehdad on 2009-07-06
I have the same problem. My laptop is Dell Vostro 1510, and half the time, Ubuntu does not recognize its keyboard at the boot time :( Any solution?

---

### Post by saurabhs on 2009-07-22
Hi
I have a DELL VOSTRO 1510. When i shutdown and start the laptop the laptop key board and mouse doesnt work but thye USB mouse works. When i restart usng the mouse it works but everytime if you start after shutting down keyboard doesnt work. 
Its irritating and if you dont have a USB mouse it never works for me.
saurabh

---

### Post by alekokk on 2009-12-23
I have the same problem with my HP laptop, using ubuntu 9.10
:(

---

### Post by electron87 on 2010-01-05
I have the same problem onn DELL Vostro 1520 .. only almost all the time the keyboard and the mousepad dont work on startup.. I have to restart to work... Please reply if any of you have solved it.. I run an Ubuntu 9.04

---

### Post by ady.david on 2010-02-04
same problem on my toshiba satellite a110-103. in my case the keyboard is never recognized but the live cd works just fine

---

