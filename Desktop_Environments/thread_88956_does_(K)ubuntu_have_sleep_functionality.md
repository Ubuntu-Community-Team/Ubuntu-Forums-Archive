---
title: "does (K)ubuntu have sleep functionality?"
date: 2005-11-11
forum: Desktop Environments
---

### Post by nrwilk on 2005-11-11
One of my favorite features of my Mac is that I never have to turn it off.  After a set timeout period, it goes to "sleep" which spins down the disks, sleeps the monitor, spins down the fans, and freezes processes.  Is there any feature like this in (k)ubuntu?  I know there are powersaving options, but these only seem to deal with the monitor.  Is there a way to spin down the hardrives and the fans?  I'd like to leave  both computers on all the time, but this PC is just too loud while I'm sleeping.

If not, it's ok.  I'd like to see that uptime counter get up over a day, though!

Thanks!

---

### Post by 23meg on 2005-11-11
It's possible with the ACPI sleep feature, but ACPI support isn't very good for all chipsets so it depends on the machine you'll be using. If things don't work out of the box you may look into compiling proper ACPI support for your machine into your kernel and chances are you'll get it going. [Software suspend]("http://www.suspend2.net/") is another option if everything fails.

In short this is a kernel feature rather than an Ubuntu one, so you should investigate whether the stock Breezy kernel has sleep/hibernate support for your chipset.

---

### Post by nrwilk on 2005-11-11
[QUOTE=23meg]In short this is a kernel feature rather than an Ubuntu one[/QUOTE]
That's what I thought.

Thank you for the suggestions!

---

### Post by ssam on 2005-11-11
it works on a lot of hardware but not all. my titanium powerbook g4 sleeps fine, i just push the lid shut, and open the lid to wake it up.

i think works on most macs running linux. it takes the kernel hackers a few months to get it working on each new machine. and it works better on ati cards than nvidia.

note. lots of linux people dont like ati because nvidia make a better closed source (binary) driver for linux than ati do. the trouble is that the closed source drivers only work on x86. if you run linux on powerpc then you have to use the opensource drivers. the opensource ati drivers tend to be better than the nvidia ones. so i like ati :-)

---

### Post by nrwilk on 2005-11-11
Well, I'm not running Kubuntu on my mac.  I guess I didn't make that too clear.
Here are my ubuntu machine's specs:

AMD Athlon 64 3500+
Abit AN8 Ultra, nForce4 Ultra chipset
nvidia 6600 TD 256MB

Kubuntu Breezy
2.6.12-9-386 kernel (using this kernel because it has the most work, support, and applications)

The driver issues and differences between ATI and nvidia cards were the main reason why I built this computer with an nvidia card.

Will this system still support sleep functionality?  Or, is it only supported under PPC architecture?

---

### Post by nrwilk on 2005-11-11
ACPI looks like it's for laptops.  It's a battery status monitor, but I'm using a desktop machine.  Does it still have some sort of sleep function that will work on a desktop box?

Software Suspend looks like it could work.

I also found a package in Adept called "hibernate" which uses ACPI, has anyone tried it?  Looks good from the description.

---

### Post by 23meg on 2005-11-11
ACPI is the name given to a protocol between the chipset, OS and CPU that manages hardware configuration and power saving operations. It's not a laptop specific thing; it exists in all recent hardware and operating systems. The hibernate package includes the command that triggers the ACPI hibernate function; whether or not it will work depends on whether or not ACPI hibernate will work on your computer.

---

### Post by nrwilk on 2005-11-11
[QUOTE=23meg]ACPI is the name given to a protocol between the chipset, OS and CPU that manages hardware configuration and power saving operations. It's not a laptop specific thing; it exists in all recent hardware and operating systems. The hibernate package includes the command that triggers the ACPI hibernate function; whether or not it will work depends on whether or not ACPI hibernate will work on your computer.[/QUOTE]

Two questions:
 * Do I need the hibernate package, or can I use ACPI directly?
 * Will it hurt anything to try ACPI?

---

### Post by 23meg on 2005-11-11
ACPI will already be installed along with Ubuntu if your hardware supports it; you won't need to do anything, and it won't hurt anything. If you'd like to hibernate your machine, you'll need that package. Check out the links below for more info on ACPI:

[http://www.acpi.info/](http://www.acpi.info/)
[http://en.wikipedia.org/wiki/ACPI](http://en.wikipedia.org/wiki/ACPI)

---

### Post by nrwilk on 2005-11-11
sucky.

> Your kernel does not have any recent Software Suspend 2 support compiled in.Please follow the HOWTO linked from [http://softwaresuspend.berlios.de/](http://softwaresuspend.berlios.de/) for
instructions on how to compile Software Suspend into your kernel.
hibernate: Aborting.

---

### Post by 23meg on 2005-11-11
It's not a big deal; if you recompile your kernel you'll get it going. It's not what it's made up to be; take a look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=85064") for some help.

---

### Post by nrwilk on 2005-11-14
> **23meg]It's not a big deal said:**
> this thread[/URL] for some help.
won't I have to recompile all my software then?  I know I'll have to reinstall the proprietary nvidia drivers, but what about everything I can download off of the repositories?

---

### Post by cus on 2005-11-15
[QUOTE=Fealos]won't I have to recompile all my software then?  I know I'll have to reinstall the proprietary nvidia drivers, but what about everything I can download off of the repositories?[/QUOTE]

You shouldn't have to - that's the great thing about Linux over certain other operating systems - the kernel is generally separated from everything else :) By way of example, I frequently tinker with the kernel and my workflow is:

change EXTRAVERSION parameter in Makefile
change kernel options through 'make menuconfig'
make-kpkg clean
make-kpkg kernel_image
dpkg -i {deb that has just been created}
install ati drivers/patch
install marvell patch
install ipw2200 patch
install madwifi
reboot

The package generated by make-kpkg adds the relevant lines to grub and the 'extraversion' tag differentiates the kernel from your existing one so you can always boot from your old kernel if you want to. If you want to uninstall it, fire up synaptic or adept and your new kernel is in the list.

---

### Post by sb73542 on 2005-11-15
For suspend to disk, try running "swsusp" or swsusp2 (can't remember which) from a command prompt.  This is more reliable, and doesn't depend on APM or ACPI.

---

### Post by 23meg on 2005-11-15
[QUOTE=Fealos]won't I have to recompile all my software then?  I know I'll have to reinstall the proprietary nvidia drivers, but what about everything I can download off of the repositories?[/QUOTE]
You definitely won't have to; all you'll need to do will be to recompile your kernel. Everything you download from the repositories is already in binary (=compiled) form and doesn't need to be recompiled. ACPI support is all about the kernel; other software just provides the userspace tools for activating certain ACPI functions.

---

### Post by nrwilk on 2005-11-16
Ok, I'm sorry to be so inquisitive, but I want to understand as much as possible.  Hopefully I'll be the one helping someone through this at a later time.

When I reinstall the proprietary nvidia driver, if I choose, for some reason, to boot into my old kernel, will my hardware acceleration then not work?  Is it possible to have a version installed for both kernels?  Maybe that's what happens already, though I am not aware of it?

---

### Post by nrwilk on 2005-11-16
double post deleted.

Dang, I keep accidentally doing this.

---

### Post by peanut butter on 2005-11-18
i have a 64 bit laptop can anyone guide me through this step by step?  Please.

---

### Post by nrwilk on 2006-01-15
new development, please don't laugh at me.

This whole time we'd been talking about suspend-to-disk.  I want to be able to sleep the computer, so I think what I need is suspend to ram.  Like what you'd get when you close the lid of a laptop.  Does this change the situation in any way?

To tell you the truth, I really don't see any point to suspend-to-disk.  I'm anal about closing everything before I shutdown anyway.

Also, with suspend-to-ram would the computer power down the fans?  Because that's the whole point.  13 fans in one case = insomnia.

---

