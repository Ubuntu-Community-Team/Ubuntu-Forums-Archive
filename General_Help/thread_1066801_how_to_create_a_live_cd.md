---
title: "how to create a live cd"
date: 2009-02-11
forum: General Help
---

### Post by Kain000 on 2009-02-11
Hey everyone, 

I'm trying to get my friend as hooked on ubuntu as I have become, and I convinced him to give it a try.

He  Booted the live cd for hearty I believe and was unable to get online.   This is a desktop so I can only assume it's a pluged in network cable.       
The first thing I would want to try is to update his kernal and packages but he cant get online.

Is there a way to take a fully patched verition of say hardy and put that on a cd such that it can be booted and installed?

I dotn have much info about the computer unfourtinally as I have never seen it but I really want to get friends to try/use linux.

---

### Post by Dr Small on 2009-02-11
Just tell me about how he is connected to the network. Is it by ethernet or wireless? Ethernet should have absolutely no problems whatsoever with connecting.

---

### Post by Kain000 on 2009-02-11
> **Dr Small said:**
> Just tell me about how he is connected to the network. Is it by ethernet or wireless? Ethernet should have absolutely no problems whatsoever with connecting.

i will ask him about that, I can only assume that it is with a cat5 cable as it is a desktop in wich case I was supprised that it didnt work, but I donno.  thanks for the reply tho.

---

### Post by Dr Small on 2009-02-11
> **Kain000 said:**
> i will ask him about that, I can only assume that it is with a cat5 cable as it is a desktop in wich case I was supprised that it didnt work, but I donno.  thanks for the reply tho.
If he's using the Ubuntu LiveCD with Gnome, then sometimes you have to go up to the network manager and click on the Connection to activate it. I've had to do that sometimes, so maybe that's all he needed to do.

---

### Post by mixmaster on 2009-02-11
> **Kain000 said:**
> Is there a way to take a fully patched verition of say hardy and put that on a cd such that it can be booted and installed?

remastersys will do this.  If you start from Intrepid you can do a 
remastersys dist
then use the .iso file it generates to make a Live CD or a persistent Live USB bootable memory stick.

---

### Post by Kain000 on 2009-02-12
> **Dr Small said:**
> Just tell me about how he is connected to the network. Is it by ethernet or wireless? Ethernet should have absolutely no problems whatsoever with connecting.

turns out it was a cat5 cable into the wall.   Most likely a network maninager thing like you suggested above.   I will give it a try.


So far as the command 
remastersys goes it spits out a live cd .iso of my current system?

---

