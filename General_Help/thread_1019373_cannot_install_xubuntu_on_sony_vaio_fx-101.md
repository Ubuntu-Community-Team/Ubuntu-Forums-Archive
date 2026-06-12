---
title: "cannot install xubuntu on sony vaio fx-101"
date: 2008-12-23
forum: General Help
---

### Post by camilo_camino on 2008-12-23
hi all, 
I am very new to linux and also xubuntu. My problem is that I cannot install xubuntu on my old sony vaio fx-101 (for specs see below). There are several problems. 
First, my cd device is very problematic and I can not change it with a new one. So I am looking for something like booting with a floppy and continuing with a cd-rom. But I do not have a floppy. So what I am looking for is booting with a cd, and continuing with an usb drive. Is it possible? Just give me a yes answer and I will try to find out how.  

Second, I can choose acpi=off mode and see the screens for personal info, clock, etc. But I could not finish that step. So I can not install xubuntu. :) What may be the possible problems? What can I do?  

Thanks...

I am using win2000 sp4 and here are the specs: 

Processor:  Celeron 600 MHz
Installed Memory  64 MB + 256 PC 133 mhz 
Display 	13.3 in. TFT Active Matrix
Bus Speed 	66 MHz
Hard Drive Capacity 	10 GB IDE 
24x CD-ROM

---

### Post by chewit on 2008-12-23
Could use a flash drive, though I doubt your laptop's BIOS is able to run flash drives.

---

### Post by camilo_camino on 2008-12-23
Thanks, but as u have already thought, it cannot boot from flash...

---

### Post by kerry_s on 2008-12-23
look here:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

i have the vaio pcg-f430 450mhz 256mb ram, i use debian lenny custom install built from the base install up.

---

### Post by camilo_camino on 2008-12-23
thanks, but I could not understand whether it requires an usb bootable machine. sorry, since I am at work now I cannot try...

Ok, I have tried and I think that it requires an usb bootable machine, now I start looking for and boot upgrades for my machine, but I am not hopeful, anyway, thanks again...

---

### Post by kerry_s on 2008-12-23
no it doesn't.

> Introduction

UNetbootin allows for the installation of various Linux/BSD distributions to a **partition** or USB drive, so it's **no different from a standard install**, only it **doesn't need a CD**. It can create a dual-boot install, **or replace the existing OS entirely**.

---

### Post by camilo_camino on 2008-12-23
ok, I will try at home, so let's see what happens. Since this is only the first step... :)

---

### Post by camilo_camino on 2008-12-24
I have tried but it did not work. it requires usb bootable bios, main board, whatever... :(

---

### Post by kerry_s on 2008-12-24
> **camilo_camino said:**
> I have tried but it did not work. it requires usb bootable bios, main board, whatever... :(

just a thought, are you sure linux is what you want? have you read up on it and understand what your getting into? you understand somethings won't just work, you have to mess with it or work around it.

---

### Post by camilo_camino on 2008-12-24
> **kerry_s said:**
> just a thought, are you sure linux is what you want? have you read up on it and understand what your getting into? you understand somethings won't just work, you have to mess with it or work around it.

well I do not know everything about linux, what I know is I want to use or at least try to use it. But I won't give up because of the fact that I cannot find anything yet. My search will go on and I am sure that I can find a way...

---

### Post by kerry_s on 2008-12-24
use unetbootin to load up partion magic to shrink the windows install and create a new partion where you can put the iso you want to install. the new partion is where you want to put the image, like as if it was a usb, but it's on the harddrive, from there you should be able to install on the other partion.

---

### Post by giancast on 2009-01-16
I am running Xubuntu in a Sony VAIO PCGN505VE. It has only 333MHz Celeron, and 128MB memory. It has an external CD-ROM and I had a hard time installing Ubuntu finally I found the ¨alternate¨ version and that one worked. I started with version 6.0 and now I am with version 8.04. I will not upgrade to 8.10 too many issues. Do a search for the ¨alternate¨ CD and give it a try.

---

