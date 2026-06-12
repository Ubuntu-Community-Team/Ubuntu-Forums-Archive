---
title: "KDE DVD problem"
date: 2005-06-21
forum: Desktop Environments
---

### Post by zeker on 2005-06-21
hello: 

 I hope someone here can help me as I have googled this topic and searched these forums and I cannot find the answer anywhere. 

I am running Kubuntu 5.04 on my iBook G4 (not completly sure of the specs) and I am very impressed. However, when I go to put a DVD in the drive the KDE deamon (kded) keeps bringing up error after error and it will not mount or recognize the DVD.  The only way to even eject the DVD is to run bash and run "eject -v /dev/dvd" and then the kded will stop crashing. 

I updated to KDE 3.4.1 but that didn't seem to fix the problem. 

Music CD's work fine, and so do data DVD's so it's not a drive issue. 

Is this maybe a conflict with copy-protection on the DVD's? (I am trying DVD movies) 

anyone know the answer or where to point me? 

thanks

-zeke

---

### Post by stevenyu on 2005-06-21
maybe something to do with autoplay?

any error messages?

---

### Post by zeker on 2005-06-21
> any error messages

I start with a normal functuioning KDE (3.4.1) desktop. 

Put a DVD into the DVD slot and the following message appears

**********************************************************************
**THE KDE CRASH HANDLER**
[B]
Short description [/B]

The application KDE Daemon (kded) chrashed and caused the signal 11 (SIGSEGV)

**What is this**

An application mostly recives the SISSEGV signal due to a bug in the application. The application was asked to save its documents
*********************************************************************

This message keeps apearing every 2 seconds until I go into bash and manualy eject the DVD as I discribed in my ealier post. The DVD does not appear on the desktop and I don't know if it gets mounted or not. 

thanks

-zeke

---

### Post by zeker on 2005-06-27
I am still working on this to no avail. 

I downloaded ogle to see if that would make a difference but I still can't even get the DVD to load and appear on the desktop without getting the error message. I don't know if this is a Kubuntu problem, an ibook problem, or a KDE problem. 

any thoughts?

- zeke

---

### Post by fdoving on 2005-06-27
I have a ibook g4 running kubuntu, and i can play dvds just fine. Could you dvd be broken somehow? Did you install the needed packages to have dvd playback? - [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by zeker on 2005-07-18
Thanks for the help but still no go

I have all the stuff installed from the restricted formats:

libdvdcss2
regionset
totem
xine

I have my drive set for DMA 

and yet I still get a crash every time I put a movie-dvd in the drive. 

any more thoughts?

-zeke

---

### Post by barnaclebarnes on 2005-09-06
Did you ever get this fixed? I am having a similar problem on my Powerbook G4. I tried to put the Kubuntu Install DVD in the drive and it crashes kded with the same message. I have also tried a region free Movie DVD and still have the same problems.

Anyone else have any ideas?

Thanks,
Glen

---

### Post by beefsprocket on 2005-09-06
Tried KDE 3.4.2?

---

### Post by barnaclebarnes on 2005-09-07
[QUOTE=beefsprocket]Tried KDE 3.4.2?[/QUOTE]

Nope. But I'm happy to try. How do I install KDE 3.4.2? It doesn't seem to show up in Synaptic. Do I have to add another repository?

Thanks,
Glen

---

### Post by Gezzer on 2005-09-07
[QUOTE=][/QUOTE]
 add this to the etc/apt/sources.list

##KDE342
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
deb-src [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

then in a konsole
sudo apt-get update

open synaptic and install the upgrades ...

---

### Post by barnaclebarnes on 2005-09-08
[QUOTE=Gezzer]add this to the etc/apt/sources.list

##KDE342
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
deb-src [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

then in a konsole
sudo apt-get update

open synaptic and install the upgrades ...[/QUOTE]

Just tried that but it seems as though there are no packages available for PPC. If you check the URL [http://kubuntu.org/hoary-kde342/dists/hoary-updates/main/binary-powerpc/](http://kubuntu.org/hoary-kde342/dists/hoary-updates/main/binary-powerpc/) there is no package.gz file there. Do you know if anyone else has compiled packages for PPC?

---

### Post by zeker on 2005-11-07
Hello all. 

 I left this alone for a while but now I have come back. I have installed breezy badger over my hoary hedgehog in the hope that this upgrade would fix this problem. 

Nope. 

I am still crashing wheever I put the DVD in. 

Again, I have the most up-to-date packages, including 3.4.2, dvdcss and ogle,xine and totem. I have dma turned on with hdparm. 

Any more thoughts on this problem?

---

### Post by zeker on 2005-11-07
I found this bug:

[http://lists.ubuntu.com/archives/kubuntu-bugs/2005-June/000782.html](http://lists.ubuntu.com/archives/kubuntu-bugs/2005-June/000782.html)

seems to be a problem for more than just me. Any thoughts on how to find out if this bug has been fixed?

---

