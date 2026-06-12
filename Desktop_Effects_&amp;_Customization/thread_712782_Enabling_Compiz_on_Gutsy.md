---
title: "Enabling Compiz on Gutsy"
date: 2008-03-02
forum: Desktop Effects &amp; Customization
---

### Post by mlyons16 on 2008-03-02
Hello,

I understand that Gutsy now has the packages for compiz already included. How do I enable compiz tho?

I've done some googling and came across this:

[http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200](http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200)

and easily enough:
> 
```
sudo aptitude install compizconfig-settings-manager
```

This will add an entry to your System > Preferences menu listed as “Advanced Desktop Effects Settings”.

Make sure that you have “extra effects” turned on by navigating to System > Preferences > Appearance, selecting the Visual Effects tab, and selecting Custom at the bottom. Clicking the Preferences button will also launch the Compiz Config Settings Manager.

First, I know I have to enable the restricted device for Nvidia, then go into synaptic and find the packages. Although, the compiz config settings manager package isn't in there.. Can i just install it thru that command line then?

And, does anyone know any good instructions otherwise to enable compiz in gutsy?

---

### Post by NightwishFan on 2008-03-02
search "compiz" in synaptic

The compiz config settings manager should be in there. Or just use the command in the terminal.

sudo apt-get install compizconfig-settings-manager

You can also get emerald, which is a window decorator, however it is not required.

---

### Post by mlyons16 on 2008-03-02
Ya, okay... I'll give that a shot. I'm presently in Vista at the moment :( lol. So even if the package, "compizconfig-settings-manager" isn't showing up in synaptic, then using the command line is an alternate procedure?

Then once its enabled, I can eitehr go alt f2 ccsm, or appearance>visual effects>custom (preferences) right?

---

### Post by NightwishFan on 2008-03-02
Or go to appearances and choose custom. Then configure it there.

---

### Post by Iam138 on 2008-03-02
> **mlyons16 said:**
> Ya, okay... I'll give that a shot. I'm presently in Vista at the moment :( lol. So even if the package, "compizconfig-settings-manager" isn't showing up in synaptic, then using the command line is an alternate procedure?

Then once its enabled, I can eitehr go alt f2 ccsm, or appearance>visual effects>custom (preferences) right?

 Right click>Change Desktop Background>Visual effects>Custom>preferences or System>Preferences>Advanced Desktop Effects Settings.

---

### Post by mlyons16 on 2008-03-18
> **NightwishFan said:**
> search "compiz" in synaptic

The compiz config settings manager should be in there. Or just use the command in the terminal.

sudo apt-get install compizconfig-settings-manager

You can also get emerald, which is a window decorator, however it is not required.

Hey, I've tried both of those and I'm presently running off the Ubuntu 7.10 Live CD. When I open up Synaptic and look in my repositories, its empty?!

I can't install thru synaptic or terminal because the packages aren't there because no repos exist. help.

---

### Post by NightwishFan on 2008-03-18
You cannot install anything off the live cd.

---

### Post by mlyons16 on 2008-03-18
> **NightwishFan said:**
> You cannot install anything off the live cd.

So if I actually install, then the repos will be there for me to install?

---

### Post by NightwishFan on 2008-03-18
Yes.

---

### Post by mlyons16 on 2008-03-18
Hey, so I installed Ubuntu 7.10... I went to synaptic to install the compiz config settings manager, and its not there.. I reloaded, but still not there.

---

### Post by NightwishFan on 2008-03-18
Open a terminal and do this command. If it fails check your software sources, although they should be enabled on a fresh install.
```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```
Or just do a search for only compiz in synaptic.

---

### Post by mlyons16 on 2008-03-18
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager


That's what it said to me after I typed that command.

---

### Post by NightwishFan on 2008-03-18
Check to see if you have your software sources enabled. It is above Synaptic.

---

### Post by mlyons16 on 2008-03-18
In my Third-Party software tab in Software Sources (repositories), I have checked:

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy (partner)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy (partner) (Source Code)

What gives?? I can't even click in Firefox: Help > Check for Updates..., that doesn't work

This all has to be related.

---

### Post by NightwishFan on 2008-03-18
Perhaps use another mirror.

I gotta go for now someone can likely help you. Good luck.

---

### Post by mlyons16 on 2008-03-19
Ya, I know that one of the original features of 7.10 was that it was gonna have compiz effects enabled by default (or at least the packages preinstalled)... but for whatever reason, I can't seem to get these codes to work

[cudo]sudo apt-get update [/cudo] (to reload the repositories, or I can click reload on the Synaptic)

then 

```
sudo apt-get install compizconfig-settings-manager 
```

but it produces the error that the package doesn't exist. I have all of my Ubuntu updates, and everything besides this is working fine. I'm thinking that maybe I need another mirror to add to my thirdparty software so that i can get this up and running.

---

### Post by mlyons16 on 2008-03-19
Ya, I know that one of the original features of 7.10 was that it was gonna have compiz effects enabled by default (or at least the packages preinstalled)... but for whatever reason, I can't seem to get these codes to work

```
sudo apt-get update 
``` (to reload the repositories, or I can click reload on the Synaptic)

then 

```
sudo apt-get install compizconfig-settings-manager 
```

but it produces the error that the package doesn't exist. I have all of my Ubuntu updates, and everything besides this is working fine. I'm thinking that maybe I need another mirror to add to my thirdparty software so that i can get this up and running.

---

