---
title: "Switching to 'i686' kernel."
date: 2005-07-29
forum: Desktop Environments
---

### Post by z-vet on 2005-07-29
Hi all.
Since i have Kubuntu running on i686 machine i want to have an 'i686' kernel installed instead of default 'i386'. So my question is: which packages i need to install exactly?

---

### Post by jasmuz on 2005-07-29
you need to have this:

linux-image-2.6.10-5-686

Download it via Synaptic or sudo apt-get install

---

### Post by z-vet on 2005-07-29
Thanks, jasmuz. Just wanted to be sure... :)

---

### Post by hod139 on 2005-07-29
You will also most likely want linux-restricted-modules-686

---

### Post by vedro on 2005-07-29
ellow

I use  2.6.10-5-386 kernel on my laptop... What are the advantages of the 2.6.10-5-686 over the 2.6.10-5-386 kernel?

My laptop is a ThinkPad R40 - Centrino proc, which is a 686, or?

And am I risking system problems with a upgrade?

have a nice day,
vedro

---

### Post by c0rderr0y on 2005-07-29
what does 

linux-restricted-modules-686

do?

---

### Post by Xian on 2005-07-29
[QUOTE=c0rderr0y]what does 

linux-restricted-modules-686

do?[/QUOTE]

It includes the following modules:

 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusba, fcpci
 - fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)

These modules are "restricted" because they are not available under a completely Free licence.

---

### Post by c0rderr0y on 2005-07-29
oooh i see that xian i'm just not too savy with the linux terms.....

---

### Post by Xian on 2005-07-29
[QUOTE=c0rderr0y]oooh i see that xian i'm just not too savy with the linux terms.....[/QUOTE]
A real world example.... You'd need the restricted-modules if you
wanted to install the nVidia drivers on your system using 
the corresponding packages in Synaptic.

---

### Post by c0rderr0y on 2005-07-29
hmm now I'm more confused what do the nVidia drivers need from that? just wonder  ing I want to understand your example.

---

### Post by Xian on 2005-07-29
[QUOTE=c0rderr0y]hmm now I'm more confused what do the nVidia drivers need from that? just wonder  ing I want to understand your example.[/QUOTE]
The _source_ nVidia drivers don't need a thing...
Like I said, it is for the gfx packages that are in Synaptic.

Think of it as a dependent library. They need each other.
[How-To Install nVidia Grapics Drivers](http://ubuntuguide.org/#installnvidiadriver) the Ubuntu way.

---

### Post by vedro on 2005-07-30
ellow

upgradet to 2.6.10-5-686 and it works like a charm :)

have a nice day,
vdero

---

### Post by z-vet on 2005-07-30
Installed an 'i686' package and restricted modules too. Everything works fine.

---

### Post by hyperair on 2007-05-24
There doesn't seem to be a 686 package for Feisty. When I installed the metapackage linux-686, it installed the generic kernel instead! It did say in the package manager that linux-686 package had been obsoleted by the linux-generic package, so does that mean that linux-generic is optimized for i686 architectures?

---

### Post by thayerw on 2007-05-24
The kernel in Feisty is generic.  It will automatically detect which architecture you are running and utilize the options for said processor.  There's no longer any need to specify which version you want.

Now, as for whether you are truly getting i686 performance, I doubt it.  I've been trying to figure that out myself.  What I do know is that the majority of applications in the repos (if not all) are compiled for i386, so regardless what your kernel is the programs aren't going to be i686 optimized.  For that, you should probably look at Arch Linux, but I must warn you that Arch isn't exactly user-friendly.  You have to customize just about everything in the system.  I tried it over the May long weekend and honestly I didn't notice much of a speed difference despite what a lot of Archers say.

[http://www.archlinux.org/](http://www.archlinux.org/)

---

