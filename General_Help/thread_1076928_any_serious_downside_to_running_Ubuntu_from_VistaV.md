---
title: "any serious downside to running Ubuntu from Vista/VirtualBox??"
date: 2009-02-21
forum: General Help
---

### Post by haiku88 on 2009-02-21
recently bought a Sony Vaio JS all-in-one and the Ubuntu intel video drivers won't work with it, have to run VESA safe mode...spent a lot of time trying to make it work to no avail and a search here showed this is a common problem...hopefully down the line a driver update will fix it.
Anyway, got fed up and am now running 32 bit Ibis from within Vista using VirtualBox, even full screen at native resolution with a few tweaks.  No doubt performance is is decreased, but for most of what I do (web surfing, web radio, etc) it works fine and I'm giving some thought to abandoning the dual boot setup.  FWIW dual booted Ubuntu and XP for a few years on my last computer so I'm fairly familiar with Ubuntu.
so....any thoughts on pros and cons of sticking with the VirtualBox within Vista setup?

---

### Post by theozzlives on 2009-02-21
Why use VirtualBox in Vista when you got WUBI?

---

### Post by haiku88 on 2009-02-21
> **theozzlives said:**
> Why use VirtualBox in Vista when you got WUBI?

AFAIK WUBI would use the Ubuntu Intel video drivers and I would still have video/display problems...did consider that though....or am I wrong about the drivers?

---

### Post by haiku88 on 2009-02-22
FWIW finally got my Jaunty partition to work right after making several mods to the xorg.conf file.  From what I've read WUBI does indeed use the Ubuntu video drivers, so that would not have been a solution in itself.  Am very happy to now have a real Ubuntu installation, but the Vista/VirtualBox install was worth it anyway, like having a Linux option from within Windows...:)

---

### Post by yther on 2009-02-22
The most likely down side would be performance, due to being in a virtual machine, but if your host machine is powerful enough it might not even be a problem.  I had Kubuntu running in a VirtualBox VM on Vista for a while; I used it to check out questionable web sites without endangering my Windows system.  :)  (If anything would happen to break, I could just revert to the previous snapshot&#8212;much better than System Restore!)  In fact, due to the Snapshot feature of VirtualBox, it might even be *better* to install it that way while you are learning to use it.  Before doing a massive upgrade, for example, you could take a snapshot of your VM, and if things get hopelessly broken you just discard the updated version and try something else, rather than having to try to repair the damage.

So... down side?  I don't think so!  :D

---

### Post by bgates on 2009-02-22
I think just performance... 

I did the opposite.  I have Windows needs but they are very few, and I never could really get some of them working on Vista anyway.  So I made a VirtualBox of Windows 2000 within Ubuntu.  I haven't booted Vista for weeks now.  The only thing is that since it's both a VirtualBox and Windows, it is impractical to schedule Windows Updates and virus definitions.  So I make sure to update those manually whenever I boot it.

---

