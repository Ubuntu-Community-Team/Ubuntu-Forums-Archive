---
title: "Kernel compilation - karmic"
date: 2010-02-11
forum: Desktop Environments
---

### Post by goro4111 on 2010-02-11
Hi,

I compiled the kernel myself (2.6.31.20). I only disabled some few things (e.g. **[COLOR=Blue]DMA, SATA[/COLOR]**) from .config as my system does not support ide.

I also update-initramfs to update the initramfs for the new kernel.

Everything seems ok, but when I try to boot with my system I get the following error:
"**ALERT! : dev/hda2 does not exist"**Checking dmesg, I can also see the following error messages:
[B]udeve[87]: segfault at 1dcb.. ..... error 6 in libc.so.6
segmentation fault
[/B][B]udevadm[90]: segfault at ..... error 6 in libc.so.6
segmentation fault[/B]

It seems that due to these errors, the system is not able to mount the filesystem, is that correct?

Why would I get this segmentation fault in my libc? the kernel compilation and initramfs were not indicating any problem.

Please help ...

---

### Post by oldefoxx on 2010-02-12
It may not be entirely safe to remove drivers from the kernel, simply because what is said about things is not always what is actually done.

As an example of this, my PCs are all reported as having /dev/sd* drives,
when actually they are either partitions on existing SATA or EIDE drives.
And since technology exists to convert from either SATA interfaces to IDE and back, and OEM might design a motherboard to go either way at the preference of certain venders.  That way the venders can use up a stock of IDE drives in addition to shifting to the newer SATA.

Now you might think that the "s" in /dev/sd* stands for SATA, but actually it stands for SCSI, a peripheral interface protocol that has largely gone out of fashion.  Calling it SCSI just means ... I don't know.  Maybe an existing group of routines to work with attachable drives has proved so worthy that they simply added some way to interface SCSI code to either a SATA or EIDE drive and not have to write all that code over again.

It's hard to say.  But the kernel is what it is, and proven well enough that most merely determine what they want to go on top of it, not change it themselves.  PCs today have so much processing power, memory, and storage space that they could make a Linux disto thousands of times larger and it would hardly be meaningful in terms of what is required from the hardware in order for it to run.

Linux, unlike with Windows, is not loaded with bloatware just to convence users that they need to buy the latest and greatest, Linux is generally lean and efficient, meaning it is generally tightly coded with just what is deemed necessary embedded inside.  So I am not sure your apparent goal to trim it even more is even necessary.

And something else to consider, is that not only does a stripped down Linux kernel put you outside the norm, but may result in other difficulties as time wears on, because you never know when something might be called for that you decided was unnecessary and took out. I mean here you are, already asking for assistance, mostly to explain why what you did may have somehow related to something unexpected and not desired, so this is certainly a case in point.

There is an old saying, you know.  Leave well enough alone.  Too bad some people in government never paid attention, and you can see the mess we've gotten into as a result.

---

### Post by goro4111 on 2010-02-12
Sorry my bad, I must have been drunk when I wrote this.

I did not disable IDE (of course not :) ) I disabled DMA support as my old mobo does not support DMA.

I also disabled SATA as I have not SATA interfaces nor SATA Harddisk in my setup.

Help is still needed, thanks

---

### Post by goro4111 on 2010-02-14
Guys, please any help on this.

I observe the same everytime I compile the kernel. I used the following steps for the compilation: [http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/)

I compile the 2.6.31-20.57 kernel and followed all the steps. Everything seems fine (no errors at all). Though I'm still dropping to shell and getting the (initramfs). And I still get the segfault error in libc.so.6 when running udevd...

---

### Post by falconindy on 2010-02-14
You may not have SATA hardware, but its the SATA kernel module that is called for creating both PATA and SATA hard drive device nodes.

---

### Post by goro4111 on 2010-02-14
> **falconindy said:**
> You may not have SATA hardware, but its the SATA kernel module that is called for creating both PATA and SATA hard drive device nodes.

Thanks falconindy for your reply. In my last compilation I did not remove SATA kernel modules. Though I still see the same issue. libc.so.6 is causing a segmentation fault when called by udevd.

I uncompressed my initramfs and checked the lib directory, libc.so.6 is there and it has the same size as the one on the build system.

---

### Post by falconindy on 2010-02-14
Without posting your attempted kernel config plus a fairly verbose lspci and lsmod on a working kernel, it's really hard to diagnose the problem. Kernel compilation is something that requires an in depth knowledge of your own hardware, how the kernel operates, and most of all, precision and patience.

---

### Post by goro4111 on 2010-02-14
Ok, so I attached the readouts.tar.gz file. It includes the .config file for the new kernel (renamed it to kernel.config) and lspci_lsmod file with the verbose readouts, also uname -a on the current version of the kernel.

lspci_lsmod is also show here for speedy:

```

xboard@ubuntu:~$ uname -a
Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
xboard@ubuntu:~$
xboard@ubuntu:~$
xboard@ubuntu:~$
xboard@ubuntu:~$
xboard@ubuntu:~$ sudo lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 81)
        Flags: bus master, medium devsel, latency 8
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [a0] AGP version 2.0
        Capabilities: [c0] Power Management version 2
        Kernel driver in use: agpgart-via
        Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: dfd00000-dfefffff
        Prefetchable memory behind bridge: cfb00000-dfbfffff
        Capabilities: [80] Power Management version 2
        Kernel modules: shpchp

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
        Subsystem: VIA Technologies, Inc. VT82C686 [Apollo Super South]
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: [c0] Power Management version 2
        Kernel driver in use: parport_pc
        Kernel modules: parport_pc

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at ff00 [size=16]
        Capabilities: [c0] Power Management version 2
        Kernel driver in use: pata_via

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
        Subsystem: First International Computer, Inc. Device 1234
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at d000 [size=32]
        Capabilities: [80] Power Management version 2
        Kernel driver in use: uhci_hcd

00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
        Subsystem: First International Computer, Inc. Device 1234
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at d400 [size=32]
        Capabilities: [80] Power Management version 2
        Kernel driver in use: uhci_hcd

00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
        Subsystem: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI]
        Flags: medium devsel, IRQ 9
        Capabilities: [68] Power Management version 2
        Kernel modules: via686a, i2c-viapro

00:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
        Subsystem: Ensoniq ES1371 [AudioPCI-97]
        Flags: bus master, slow devsel, latency 64, IRQ 10
        I/O ports at cc00 [size=64]
        Capabilities: [dc] Power Management version 1
        Kernel driver in use: ENS1371
        Kernel modules: snd-ens1371

00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
        Flags: medium devsel, IRQ 11
        I/O ports at c800 [size=32]
        Kernel driver in use: ne2k-pci
        Kernel modules: ne2k-pci

00:0e.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)
        Subsystem: Giga-byte Technology Device a000
        Flags: bus master, slow devsel, latency 64, IRQ 11
        I/O ports at c400 [size=64]
        Capabilities: [dc] Power Management version 1
        Kernel driver in use: ENS1371
        Kernel modules: snd-ens1371

00:0f.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at dfcfc000 (32-bit, prefetchable) [size=4K]
        Capabilities: [44] Vital Product Data <?>
        Capabilities: [4c] Power Management version 2
        Kernel driver in use: bttv
        Kernel modules: bttv

00:0f.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at dfcfd000 (32-bit, prefetchable) [size=4K]
        Capabilities: [44] Vital Product Data <?>
        Capabilities: [4c] Power Management version 2

01:00.0 VGA compatible controller: S3 Inc. ProSavage KM133
        Subsystem: S3 Inc. ProSavage KM133
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 3
        Memory at dfe80000 (32-bit, non-prefetchable) [size=512K]
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at dfe70000 [disabled] [size=64K]
        Capabilities: [dc] Power Management version 2
        Capabilities: [80] AGP version 2.0
        Kernel modules: savagefb

xboard@ubuntu:~$
xboard@ubuntu:~$
xboard@ubuntu:~$
xboard@ubuntu:~$ sudo lsmod
Module                  Size  Used by
iptable_filter          3100  0
snd_ens1371            22016  0
bttv                  118996  0
ip_tables              11692  1 iptable_filter
ir_common              48512  1 bttv
gameport               11368  1 snd_ens1371
x_tables               16544  1 ip_tables
snd_rawmidi            22208  1 snd_ens1371
i2c_algo_bit            5760  1 bttv
snd_seq_device          6920  1 snd_rawmidi
v4l2_common            17500  1 bttv
videodev               36736  2 bttv,v4l2_common
snd_ac97_codec        101216  1 snd_ens1371
v4l1_compat            14496  1 videodev
videobuf_dma_sg        12544  1 bttv
ac97_bus                1532  1 snd_ac97_codec
videobuf_core          17952  2 bttv,videobuf_dma_sg
btcx_risc               4740  1 bttv
snd_pcm                75296  2 snd_ens1371,snd_ac97_codec
ppdev                   6688  0
tveeprom               11872  1 bttv
snd_timer              22276  1 snd_pcm
lp                      8964  0
parport_pc             31940  1
snd                    59204  6 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm,snd_timer
parport                35340  3 ppdev,lp,parport_pc
soundcore               7264  1 snd
shpchp                 32272  0
snd_page_alloc          9156  1 snd_pcm
psmouse                56180  0
via_agp                 7932  1
via686a                12744  0
serio_raw               5280  0
agpgart                34988  1 via_agp
i2c_viapro              7312  0
usb_storage            52544  0
ne2k_pci                8512  0
8390                    9756  1 ne2k_pci
floppy                 54916  0

```

---

### Post by goro4111 on 2010-02-16
I'm actually suspecting that the issue is related to selectin configure standard kernel features (for small systems) in General Setup in kernel configuration. If I include it in  the kernel configuration then the compiled system will cause the segmentation fault. If I remove it (which is default) then it will not fail. this is only my suspect... I need to test more. 
 
Any thoughts?

---

### Post by goro4111 on 2010-02-21
> **goro4111 said:**
> I'm actually suspecting that the issue is related to selectin configure standard kernel features (for small systems) in General Setup in kernel configuration. If I include it in  the kernel configuration then the compiled system will cause the segmentation fault. If I remove it (which is default) then it will not fail. this is only my suspect... I need to test more. 
 
Any thoughts?

Wrong suspicion. I compiled 2.6.31-15.49 with and without standard kernel features (for small systems) and both works fine. My problem is that this kernel version does not include the fix for my mobo !!! And compiling a newer kernel (2.6.31-20.57) with exactly same .config gives the lib6 segmentation fault. Gonna get something in the middle and compile again.

Still open for comments/suggestions.

---

