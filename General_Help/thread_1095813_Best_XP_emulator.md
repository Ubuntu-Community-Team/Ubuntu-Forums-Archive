---
title: "Best XP emulator?"
date: 2009-03-14
forum: General Help
---

### Post by pewterbot9 on 2009-03-14
Linux newbie here. :grin:

I know about Wine, but never used it. Here is a page that lists additional Windoze emulators:

[http://www.freebyte.com/operatingsystems/#emulators](http://www.freebyte.com/operatingsystems/#emulators)

I'm interested in an XP emulator for Ubuntu 8.10, that works well with unsupported peripherals, such as scanners and printers. Is the ol' standard Wine best for that, or some other? Here's a list of free Windoze emulators, on that page:

Bochs
VirtualBox
Wine

(Bochs is located here: [http://bochs.sourceforge.net/](http://bochs.sourceforge.net/), VirtualBox here: [http://www.virtualbox.org/](http://www.virtualbox.org/) .)

Is one emulator perhaps better at handling unsupported drivers, than the other two? TIA.

Or would NDIS wrapper be the better solution? I have been advised by hackers-in-the-know, to avoid that program like a plague...not for newbies.

---

### Post by labinnsw on 2009-03-14
Not sure about the best, but I use QEMU and pass my files via a USB defice to and from Ubuntu. That takes care of all my printing and scanning needs.

---

### Post by hikaricore on 2009-03-14
There really is no such thing as a Windows or "XP" emulator...

What you're talking about is a virtual machine and it will mostly only support the hardware that the underlying OS does.
Virtual machines have come a long way but don't expect them to be a perfect replacement for running Windows alone.

---

### Post by pewterbot9 on 2009-03-14
Thanks for all the advice! I will install QEMU, and see what happens. I haven't even plugged in my USB scanner, I'm so new to Linux...just installed Intrepid Ibex four days ago! Very pleased with all the improvements in user-friendliness since the last time I ran a Linux distro about five years ago. I am definitely offa Windoze for good. :)

---

### Post by LegendofTom on 2009-03-14
And just because we can, Wine Is Not an Emulator.

---

### Post by RD1 on 2009-03-14
> that works well with unsupported peripherals, such as scanners and printers.

I run XP in VirtualBox and am able to use my old flatbed scanner that is unsupported in Linux.

Get the Sun version for full USB support.

---

### Post by snova on 2009-03-14
> **pewterbot9 said:**
> I'm interested in an XP emulator for Ubuntu 8.10, that works well with unsupported peripherals, such as scanners and printers. Is the ol' standard Wine best for that, or some other?

Wine is used to run applications, it won't help with drivers.

> Bochs
VirtualBox
Wine

Forget Bochs, it's an emulator (meaning, it runs CPU instructions one-by-one, its horribly slow for most purposes).

VirtualBox is a virtualization program, meaning it essentially creates a computer inside your computer, and can run XP inside it. This is probably your best bet. However, if the devices are USB, you'll need the version from [their website]("http://www.virtualbox.org/"), as the version in the repos doesn't support USB.

See the Virtualization subforum, particularly the sticky there: [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

> Or would NDIS wrapper be the better solution? I have been advised by hackers-in-the-know, to avoid that program like a plague...not for newbies.

Ndiswrapper makes it possible to use Windows wireless card drivers on Linux, it won't help with printers or scanners.

---

### Post by dragos240 on 2009-03-14
> And just because we can, Wine Is Not an Emulator.

i was just about to say that!

---

### Post by pewterbot9 on 2009-03-14
A lot of wisdom offered here. I will take all the advice to heart: thanks everyone!

---

### Post by pewterbot9 on 2009-03-15
> **RD1 said:**
> Get the Sun version for full USB support.

Whaddya know: Sun Microsystems Virtualbox 2.0.4_OSE is already installed in my Ubuntu system! Can't activate the "check for update" option, though. Assuming I can as root...which I'll look into later. (I'm on the 'net right now, away from home.)

Thnx!

---

