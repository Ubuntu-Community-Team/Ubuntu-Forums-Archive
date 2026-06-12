---
title: "Is there an Open Source VMware like product"
date: 2006-05-10
forum: Desktop Environments
---

### Post by everett3rd on 2006-05-10
I am a linux noobie (1 week and counting.)

I have one program that I have not found a Linux alternitive for.
Army Builder ( I'm a Warhammer nut too.)

Is there a open source VMware style product I can use to run XP just so I can use this program.

OR does anybody know of an alternate Army Builder type product
(I'd even buy this) that will let me dump XP 100%?

Thanks for the help.
-Everett3rd

---

### Post by NESFreak on 2006-05-10
try Qemu [https://wiki.ubuntu.com/Installation/QemuEmulator](https://wiki.ubuntu.com/Installation/QemuEmulator)

---

### Post by zenandruby on 2006-05-10
Try Xen: [http://www.cl.cam.ac.uk/Research/SRG/netos/xen/](http://www.cl.cam.ac.uk/Research/SRG/netos/xen/) ;)

---

### Post by lordofkhemenu on 2006-05-10
2nd vote for Qemu.

---

### Post by blair on 2006-05-11
Last Month's (May 06) Linux Journal had a feature on this very subject. There are several options, each w/ pros and cons.

- VMware: runs anything on anything
- User-Mode Linux: Runs linux on linux
- QEMU: Runs anything on anything
- Xen: Runs linux on linux. Note you specifically have to modify (port) the OS so that it runs on Xen. Only a handful of distros have done this so far. 

So if you want to run XP on Linux, your only options are  really VMware and QEMU. 

For a QEMU links page, see [www.linuxjournal.com/article/8884](www.linuxjournal.com/article/8884)

Warning: The article (and the QEMU site) indicates that KQEMU is a QEMU accelerator that makes a big performance difference. However you must compile the source QEMU to use the QEMU/KQEMU combination; You cannot just download the two compiled programs and expect them to work together. Compiling QEMU apparently is easier said than done with lots of little tweaks required to get it right.  My suggestion is just use QEMU (already compiled) and get familiar with it. If you have a fast machine, the performance may be good enough you don't even need to mess with compiling it. 

good luck

---

### Post by everett3rd on 2006-05-18
Well after trying these solutions with little success....

I am going to homebrew my own solution...

It'll be good for me, build character and all that....:D 

Thanks for all the help.

---

### Post by aysiu on 2006-05-18
I know VMWare may not be open source, but it does have a Linux port, which was included with the April 2006 issue of *Linux Format* magazine.

---

### Post by tkjacobsen on 2006-05-18
Qemu is good, and easy to use. It might be a good idea to compile and install the kqemu kernel module though, it will improve the speed significantly.


Try to take a look at this post
[http://www.ubuntuforums.org/showthread.php?t=134541&page=2&highlight=dapper+kqemu](http://www.ubuntuforums.org/showthread.php?t=134541&page=2&highlight=dapper+kqemu)

---

### Post by Sniffer on 2006-05-18
QEMU can be VERY SLOW with XP on it....:-| 

My personal experience last time i have tried...


VMWARE by me deals with XP very fast in relation to QEMU...

---

### Post by Elijah on 2006-05-19
I've been working with qemu just to run IE (web development)... how can that run games like what the threadstarter wanted? I thought qemu is using a specific set of hardware to emulate?? 

> 
The QEMU PC System emulator simulates the following peripherals:

    * i440FX host PCI bridge and PIIX3 PCI to ISA bridge
    * Cirrus CLGD 5446 PCI VGA card or dummy VGA card with Bochs VESA extensions (hardware level, including all non standard modes).
    * PS/2 mouse and keyboard
    * 2 PCI IDE interfaces with hard disk and CD-ROM support
    * Floppy disk
    * NE2000 PCI network adapters
    * Serial ports
    * Creative SoundBlaster 16 sound card
    * ENSONIQ AudioPCI ES1370 sound card
    * Adlib(OPL2) - Yamaha YM3812 compatible chip
    * PCI UHCI USB controller and a virtual USB hub. 


---

### Post by Jason_25 on 2006-05-19
With my experience in qemu, it's hard to get files you have created in the guest os out to the host os (ubuntu).  In the packaged version .8.0 I can get usb sticks to show up in windows 2000, but they don't work correctly.  In .8.1 from the website, I can not get usb sticks to work at all.  I have also tried to add a directory as a virtual FAT drive.  In both versions, moderate disk activity will crash the emulator.  So, it works great and is fast enough, but I can't easily move files from inside the emulated image out to ubuntu.

---

