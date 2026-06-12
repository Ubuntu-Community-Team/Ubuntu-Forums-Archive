---
title: "Compiz Questions"
date: 2008-01-01
forum: Desktop Effects &amp; Customization
---

### Post by xtrumanx on 2008-01-01
Hi there. I keep coming back and trying out Ubuntu but haven't switched yet. I'm trying to get a feel for Compiz but am having a problem getting it to install. I'm using Gutsy Gibbon and am trying to get the compizconfig-settings-manager to install (following [this tutorial]("http://ubuntu-tutorials.com/2007/10/04/compiz-fusion-on-ubuntu-710-gutsy-gibbin/")) but when I type the terminal command ```
sudo aptitude install compizconfig-settings-manager
``` to download the settings manager I get the following: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "compizconfig-settings-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done
```

I'm thinking it has something to do with enabling/adding certain repositories but I'm pretty clueless when it comes to those things. 

Also, if someone could enlighten me about something related: do I have to install proprietary drivers before compiz would become fully functional? Currently, Ubuntu recognizes my Radeon 9600XT and I got max the resolution for my monitor (1280x1024) and the extra visual effects working fine but I had a problem doing so with my last Ubuntu installation when using compiz. Any help appreciated.

---

### Post by eilu on 2008-01-01
not sure if this is what you meant, but this is a very good step-by-step guide:
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)
hope that helps.

---

### Post by FuturePilot on 2008-01-01
Make sure you have all the software sources enabled under System>Administration>Software Sources.

---

### Post by xtrumanx on 2008-01-01
All software sources are enabled but I noticed that the Synaptic Package Manager fails to download the files when I press reload. Eilu link also does nit work. The internet is working fine (as I am posting this on Ubuntu), I have a feeling something is wrong with Ubuntu as this is a fresh install but I have  been notified of no updates yet. Seems odd since I'm sure an update or two has probably been released since Gutsy's October release.

edit: More suspicions aroused that Ubuntu apps can't connect to the internet beside firefox. Pidgin doesn't seem to work for me but as a first time user, I'll let that slide. But what's more weird is that sudo apt-get update doesn't work as well. This is what I see when I attempt to update:
```
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Err http://archive.canonical.com gutsy Release.gpg                                c
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com gutsy Release.gpg                                   
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com gutsy-security Release.gpg                         
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
25% [Connecting to archive.canonical.com (1.0.0.0)] [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

```

---

