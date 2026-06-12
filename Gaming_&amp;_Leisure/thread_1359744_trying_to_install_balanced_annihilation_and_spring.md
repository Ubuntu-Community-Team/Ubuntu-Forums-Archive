---
title: "trying to install balanced annihilation and springdownloader"
date: 2009-12-20
forum: Gaming &amp; Leisure
---

### Post by ngage on 2009-12-20
I'm trying to install springdownloader.exe and balanced annihilation.  I installed springlobby fine from ubuntu software center.  Now I have to install the balanced annihilation mod to actually play the game.  I followed the directions to install springdownloader to install balanced annihilation from [http://trac.caspring.org/wiki/sd](http://trac.caspring.org/wiki/sd)

I downloaded springdownloader fine using this command:
wget  [http://files.caspring.org/caupdater/SpringDownloader.exe](http://files.caspring.org/caupdater/SpringDownloader.exe)

Here are my error messages:

~$ sudo apt-get install mono libmono-winforms2.0-cil
[sudo] password for user1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mono is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mono has no installation candidate

I checked synaptic and libmono-winforms2.0-cil is there, but no mono by itself.  There are a lot of packages related to the mono architecture (the linux version of C# and the .NET architecture) but I don't know which one I'm supposed to install.

The final command is supposed to be:
mono SpringDownloader.exe 

So is there an actual command called "mono" as well that's supposed to do something with springdownloader?

---

### Post by Vadi on 2009-12-20
Yeah, there is an actual command called mono. However afaik, springlobby integrates downloads anyway...

---

### Post by ngage on 2009-12-21
do you know what mono package i need besides winforms though?

springlobby keeps getting those torrent errors. it doesn't seem to be a problem on my end b/c torrents w/ transmission work fine.

---

