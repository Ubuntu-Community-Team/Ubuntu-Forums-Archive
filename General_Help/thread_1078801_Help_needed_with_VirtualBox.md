---
title: "Help needed with VirtualBox"
date: 2009-02-23
forum: General Help
---

### Post by Dj-Tempo on 2009-02-23
Hi I'm trying to find, download & install VirtualBox or some other virtual PC for linux but each time i download one I keep getting random errors i.e I just managed to find VirtualBox 1.3.8 .deb but when i tried to install it said... 

```
Error: dependancy is not satisfiable: libqt3-rt
```

I also tried VMware Workstation which wouldn't install I really need to get back to windows XP and the only way I can do that at the moment is by a Virtual PC Software, can someone please explain (in simple terms, im a linux newbie) how I should go about installing or if infact what I'm doing wrong... Thanks

Oh, and my current version of linux is "Ubuntu - 7.04 - Feisty Dawn" Incase u need to know :D

---

### Post by albinootje on 2009-02-23
> **Dj-Tempo said:**
>  I just managed to find VirtualBox 1.3.8 .deb but when i tried to install it said... 

```
Error: dependancy is not satisfiable: libqt3-rt
```
-- cut --
my current version of linux is "Ubuntu - 7.04 - Feisty Dawn" Incase u need to know :D

Very good that you mention that. 
Ubuntu Feisty Fawn, also known as 7.04, is very old.
It is recommended that you upgrade to 8.04, and after that install the latest VirtualBox.

Make sure to make backups before upgrading or reinstalling!

---

### Post by Slim Odds on 2009-02-23
Also, the open source version of VirtualBox (OSE) is in the repositories.

No need to download from some other source (once you're on a new version of Ubuntu).

---

### Post by mtopro on 2009-02-23
For the USB support in VB you will need to install it from the source.  Works good on 8.04 or 8.10 64bit.
[http://www.virtualbox.org/]("http://www.virtualbox.org/")

One thing you may want to know is VirtualBox creates a file on your harddrive that 'acts' as a separate partition when loaded through VB.  I don't believe you can load an existing operating system on another disk.

---

### Post by Dj-Tempo on 2009-02-23
> **albinootje said:**
> Very good that you mention that. 
Ubuntu Feisty Fawn, also known as 7.04, is very old.
It is recommended that you upgrade to 8.04, and after that install the latest VirtualBox.

Make sure to make backups before upgrading or reinstalling!

Ok but my CD Rom is broken and i only have two USB sticks one of 1gig, one is 2gig how can i install a more recent "Ubuntu" without CD unless its possible to create a bootable USB stick containing a more recent edition??

---

### Post by albinootje on 2009-02-23
> **Dj-Tempo said:**
> Ok but my CD Rom is broken

It should be possible, without cdrom or usb-stick, to upgrade to Gutsy/7.10 if you have a working internet connection.
Make sure to backup your data beforehand.

---

### Post by albinootje on 2009-02-23
After you've successfully upgraded to Gutsy, you can install the package virtualbox-ose from the Ubuntu repositories :
[http://packages.ubuntu.com/search?keywords=virtualbox-ose](http://packages.ubuntu.com/search?keywords=virtualbox-ose)

---

### Post by geirha on 2009-02-23
Here's instructions on how to upgrade from the no longer supported 7.04 to 7.10:
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by Slim Odds on 2009-02-24
> **mtopro said:**
> For the USB support in VB you will need to install it from the source.  Works good on 8.04 or 8.10 64bit.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

You don't have to install from source, they have .deb packages for the full free (but not open source) version.

> **mtopro said:**
> One thing you may want to know is VirtualBox creates a file on your harddrive that 'acts' as a separate partition when loaded through VB.  I don't believe you can load an existing operating system on another disk.

??? I don't really understand this.

---

### Post by carml on 2009-02-24
Maybe you need to look in System->Administraion->Synaptic Package manager the string that Virtualbox need to.;)

---

### Post by Dj-Tempo on 2009-02-24
Thanks to all of you for your help, however as a music producer Linux isn't really my thing so I've reverted back to good old n00b friendly Windows XP lol :guitar:

---

### Post by mtopro on 2009-02-24
Slim Odds.  My unclear statement was an attempt to help Dj Tempo understand how VB works.  He said:

> **Dj-Tempo said:**
> I really need to get back to windows XP and the only way I can do that at the moment is by a Virtual PC Software

It sounded like there may have been an installation of XP in another location on his computer that was trying to reach through VB rather than dual boot.

The VirtualBox creates a .vdi (virtual disk) at /home/USER/.VirtualBox/HardDisks
This file acts as new partition, but would not be the same as a dual boot install.
Did that clear anything up or are you REALLY confused now?

Glad to see Dj-Tempo got up and running.  Too bad we couldn't help you in time..  With VirtualBox you really can enjoy the best of both worlds.

---

### Post by Dj-Tempo on 2009-02-25
Nah I had entirely wiped XP after my install became corrupted with the "Virut" Viruses trouble personally I think with Ubuntu and the reason I didn't get on with it is A: Old Old Edition... 7.04 And B: Lack of experience with a linux based system call this ignorance or whatever as some people may do but when you've only been bought up with "Windows" you get stuck with it, I couldn't see a way round running programmes such as FL Studio which uses sophisticated windows based engines to perform smoothly aswell as the main programme and many of the "VSTi's" being .exe format it was simply a no go area even with using "WINE" or "CROSSOVER" the propgramme would install then mid prodution the programme would close on me causing extreme panic and stress... lol 

Anyway to all those that gave advice & help thank you all & best of luck with more experienced "Linuxers" Sadly im not one of them and unless a more user friendly version is released i cant see my self returning (How ever much i miss the lil linux penguin ;)) :lolflag:

---

