---
title: "make windows disk images with ubuntu?"
date: 2006-03-14
forum: Desktop Environments
---

### Post by geuis on 2006-03-14
I'm managing a network of around  30-40 computers with WinXP home/pro on them. However, I use ubuntu on my own workstation.

What's really annoying is how ever time one of the windows machines comes in, I have to reinstall it from scratch, download updates, etc.

What I would really like to do is get one machine configured, then make an image of the system and store that image on my workstation. From there, I want to be able to hook a new machine up to my switch and write the image to the new computer.

I'm imagining that Linux has some cool tools that will let me do this in a much more configurable(and free!) way than Norton Ghost and whatnot.

Can someone with more experience with this give me some recommendations? Ideally, I would love to just plug the computer in, run some insta-magic commands in Ubuntu, and have it start restoring. Fearing that, I can imagine booting the new machine off of a linux boot disk and have it get the image from across the network from my Ubuntu machine.

I appreciate help on this. I've got a stack of 10 machines that I need to re-image before the end of the week(we just closed 2 stores) and this will save hours of time.

--Geuis

---

### Post by ssalman on 2006-03-14
I have done the same on two laptops with SystemRescueCd[]("http://www.sysresccd.org/Main_Page") ([link]("http://www.sysresccd.org/Main_Page")) using PartImage and Samba it worked great... I read somewhere that you can do it without the compresion and copying all the empty bytes using the "dd" linux command. Google it up :)

---

### Post by geuis on 2006-03-14
I think that'll work. Thanks!

---

### Post by gibson on 2006-03-14
I tried similar a while ago, athough a point yo be noted.

You will need to make a windows image for each type of chipset..

one for VIA machines
one for SIS
one for nvidia nforce erv....


as the windows installer determines this and alters the installation slightly

other that that it works well.

another thing you can get is a reg hack that deletes the licence key information, so when you "re-install" it asks you for the key for that machine and the underlying configuration and install is unaffected but serials are unique... if you care that is ;)

thanks
 gib

---

