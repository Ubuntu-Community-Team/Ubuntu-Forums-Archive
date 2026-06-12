---
title: "absolute minimum kernel configuration"
date: 2009-01-22
forum: General Help
---

### Post by limrick on 2009-01-22
I couldn't find any posts on this subject.

8.10 intrepid

I'm trying to compile an absolutely minimal kernel,,, KERNEL not
system.

Where the kernel boots to the command prompt shell and there are
no unnecessary module/code/etc in the kernel.
I'll get the system up and then compile the drivers into it
as I go along.

If you could point me in the right direction it would be
greatly appreciated.

---

### Post by ibuclaw on 2009-01-22
Is there any particular reason for you wishing to compile one?

If you are doing it for an embedded device, that is understandable, but if you are wanting a minimal kernel for your desktop system, then you won't benefit from it. There won't be any speed increase or optimisation in your workload in doing so. Linux is modular, only the modules(drivers) of the devices that are connected to the computer will be loaded into memory.
Infact, by using a minimal kernel on your desktop, you may be causing more grief than relief. As you can, if you aren't paying attention, remove the modules needed for a, say USB device you frequently use.

Regards
Iain

---

### Post by limrick on 2009-01-22
Its for an embedded device that has compact flash,ethernet,serial,usb etc.
basicly micro pc on a board.

---

### Post by ibuclaw on 2009-01-23
Ah OK.

Makes sense then :)

You'd probably have difficulty setting this up on the physical hardware yourself (compiling a kernel may still require MBs of source code) and so you'll probably have to reside to using a Virtual machine for the initial building task.

But you can look at projects that make tiny versions of Linux:
[http://www.slitaz.org/en/get/](http://www.slitaz.org/en/get/) (Slitaz, Linux Desktop. 24MB iso).
[http://distro.ibiblio.org/pub/linux/distributions/baslinux/](http://distro.ibiblio.org/pub/linux/distributions/baslinux/) (BasicLinux3, 3MB)
But both require that you have an x86 machine.

I've never built anything on embedded devices before, but two places I'd probably start are here:
[http://en.wikipedia.org/wiki/Embedded_Linux](http://en.wikipedia.org/wiki/Embedded_Linux) (Note the **See also** section)
[http://oreilly.com/catalog/9780596002220/](http://oreilly.com/catalog/9780596002220/) (Seems like an interesting book on the subject).


Regards
Iain

---

### Post by blazemore on 2009-01-23
If you're using Ubuntu, you can build debs when you compile. You can then install these debs on the target system.

---

### Post by limrick on 2009-01-23
tinivole:

Thanks for the pointers, I am using a VMware machine


blazemore:

correct, building debs.


Thanks to both of you

---

### Post by souren on 2010-09-06
Hi Guys,

I guess I am in the same position and need a bit of help to get started.

I am trying to see if I can build an embedded Ubuntu Kernel for some of our boxes running on fairly old hardware (Pentium 100), with only 64MB of RAM.

I need to build an image and put it on a 256MB Compact Flash card, and the machine should boot up. Initially, I am happy to get a command line only version going but eventually I need to have a GUI framework as part of the installation as well.

I tried Puppy Linux but hit a few issues on bootup - ends up with a Kernel Panic, and after several attempts I couldn't really figure out what's going on.

Would really appreciate if you I can get some help on this. Thanks guys.

Cheers.
Souren

---

### Post by C.S.Cameron on 2010-09-06
Have a look at tinycore, it is only about 10000 KB.
Or Puppy.
I don't think Ubuntu will run on a 64MB Machine.

---

### Post by souren on 2010-09-06
hmmm ok. Thanks.

I tried to use Puppy...but it keeps dieing on a "Kernel Panic" on bootup. I am guessing it's having trouble doing its initial bootup from RAM perhaps...

---

