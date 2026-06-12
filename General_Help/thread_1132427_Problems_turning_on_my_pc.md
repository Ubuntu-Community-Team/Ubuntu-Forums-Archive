---
title: "Problems turning on my pc"
date: 2009-04-21
forum: General Help
---

### Post by nerotkd on 2009-04-21
First, sorry about my bad english, I'm from Argentina and I speak spanish...

I have been using ubuntu for the last 4 months, but in the last weeks a problem started:
When I turn on the pc, i hear a LOUD **BEEEEEEEEEP**, just like when you have an error for at least 25 seconds, and then the screen goes black and the system doesn't boot. But, if then I reset my PC, ubuntu boots normally...
If I reset the pc after the screen goes black, when it reboots the screen starts again with the beep.

After the problem started, ubuntu boot was with a beautiful logo and loading bar, but now it boots in a text-only mode.

The first line before the BEEEP says something of Fuse Init...

---

### Post by codeseer on 2009-04-21
Beeps are the BIOS's way of telling you something is wrong. Have you consulted your motherboard manual?

---

### Post by nerotkd on 2009-04-22
The beep starts in Ubuntu boot! In Windows I havent got any problems... And that started a few days ago...
After I select ubuntu in the grub... And its a looong beep, 20 secs~

---

### Post by codeseer on 2009-04-22
Humm. Very weird.

---

### Post by nerotkd on 2009-04-22
I forgot to say... Im using Intrepid ibex...

---

### Post by codeseer on 2009-04-22
You could try [disabling the pc speaker]("http://strabes.wordpress.com/2006/10/16/remove-the-system-beep-in-ubuntu/"). I know that probably won't fix the black screen problem, but it might take some annoyance away while troubleshooting.

Have you tried installing any themes, splash screens, etc lately?

---

### Post by nerotkd on 2009-04-22
I disabled the pc speaker... but in the boot it still sounds!
Ah! and i don't have tried to install anything strange...

---

### Post by codeseer on 2009-04-22
Try steps 1-5 here: [https://wiki.ubuntu.com/DebuggingUsplash#Debugging%20procedure]("https://wiki.ubuntu.com/DebuggingUsplash#Debugging%20procedure")

---

### Post by regor210 on 2009-04-22
nerotkd did you get it fixed?

If not you may want to check these things as well.

Have you moved your computer or disconnected your monitor lately?
If yes, see if you have another place to plug in the monitor in the back of your computer. 
like mother board > EPCI > APG.

Have you tried starting your computer using an Ubuntu live cd? 
If the live cd works fine then....

I had an issue like this with an ATI video card once.

Did this problem start after installing proprietary video drivers?
If yes, try removing  proprietary video drivers.

or 

Try starting Ubuntu in (recovery mode). If you dual Boot just use the arrows when you see the grub menu. If you do not dual Boot you will have to press the Esc key when you see Grub when you first start your computer or restart. xfix Try to fix x server. 

or

You may need to reinstall Ubuntu. If you reinstall  &#65279;Ubuntu 9.04 Jaunty Jackalope  is scheduled for release April 23, 2009 tomorrow.

---

