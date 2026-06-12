---
title: "lock up at boot (syslog)"
date: 2005-07-08
forum: Desktop Environments
---

### Post by secundar on 2005-07-08
(writing this from Hoary LiveCD)

I hate to do this but i'm a little desperate and my switching experience hasn't been all that smooth.

I have upgraded my kernel to 2.11-686 (ubuntu), Nvidia driver is 7664 and I've done something in synaptic that prevents my laptop from booting up. If I could get some pointers as to where to look for a solution that would help. At the moment things are rsyncing to a server so I am preparing for a reinstall but would like to avoid that (Mac user coming to ubuntu.)

I can try to provide more info if needed....

/var/log/mesages excerpt...
```


localhost kernel Asus Laptop ACPI Extras version 0.29
localhost kernel unsupported, trying default values, supply the developers with your DSDT
localhost kernel ACPI: AC Adapter [AC0] (on-line)
localhost kernel usb 2-1: USB disconnect, address 2
localhost kernel usb 2-1: new low speed USB device using uhci_hcd and address 3
localhost kernel input: USB HID v1.00 Mouse [1241:1111] on usb-0000:00:1d.1-1
localhost kernel ACPI: Battery Slot [BAT0] (battery present)
localhost kernel ACPI: Battery Slot [BAT1] (battery absent)
localhost kernel ACPI: Power Button (FF) [PWRF]
localhost kernel ACPI: Sleep Button (CM) [SLPB]
localhost kernel ACPI: Lid Switch [LID]
localhost kernel ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
localhost kernel ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
localhost kernel Stopping tasks: ======|
localhost kernel Freeing memory...  ^H-^H\^H|^H/^H-^H\^Hdone (813 pages freed)
localhost kernel Restarting tasks... done
localhost kernel EXT3-fs: mounted filesystem with ordered data mode.
localhost kernel kjournald starting.  Commit interval 5 seconds
localhost kernel EXT3 FS on sda2, internal journal
localhost kernel Linux agpgart interface v0.100 (c) Dave Jones
localhost kernel nvidia: module license 'NVIDIA' taints kernel.
localhost kernel ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
localhost kernel NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7664  Wed May 25 10:47:55 PDT 2005
localhost kernel Capability LSM initialized
localhost kernel cdrom: open failed.
localhost kernel NTFS driver 2.1.22 [Flags: R/O MODULE].
localhost kernel cs: IO port probe 0x0100-0x04ff: excluding 0x370-0x377 0x3b0-0x3df 0x3f0-0x3f7 0x400-0x41f 0x480-0x4bf 0x4d0-0x4d7
localhost kernel cs: IO port probe 0x0800-0x08ff: excluding 0x818-0x87f
localhost kernel cs: IO port probe 0x0c00-0x0cff: excluding 0xcf8-0xcff
localhost kernel cs: IO port probe 0x0a00-0x0aff: clean.
localhost Xprt_64 lpstat: Unable to connect to server: Network is unreachable
localhost Xprt_64 No matching visual for __GLcontextMode with visual class = 0 (32775), nplanes = 8
localhost shutdown[3759] shutting down for system reboot
localhost Xprt_64 Xprint server pid=3504 done, exitcode=0.
localhost kernel Kernel logging (proc) stopped.
localhost kernel Kernel log daemon terminating.
localhost  exiting on signal 15


```

---

### Post by alastair on 2005-07-08
The only thing that really stands out is this Xprint stuff i.e. Xprint server package :

```

Xprt_64 No matching visual for __GLcontextMode with visual class = 0 (32775), nplanes = 8
shutdown[3659] shutting down for system reboot
Xprt_64 Xprint server pid=3453 done, exitcode=0.

```

It always seems to end up a problem. So ....

See if removing it helps.

Boot - and stop at GRUB (ESC).

Select the right kernel to boot and : "e" to edit
Then "e" to edit the kernel line
Strip everything off up to the "ro" (read-only) bit - and add "single".
Then "b" to boot to single user mode.

Log in.

Remove the Xprint packages :

apt-get remove xprt


Then reboot :

reboot

and see if things improve.

---

### Post by secundar on 2005-07-08
Thanks Alastair, I will remember to steer far away from Xprint - assuming it is the culprit.

But alas, I could wait no more and I reinstalled after backing up my home folder. I think I have learned a lesson. I'm going to stick with Hoary - as strictly as possible - and not go around setting repositories willy nilly.

I assumed the problem lie in my choice of kernel: 2.6.10-686 for my centrino. That, and the Nvidia driver version 1.7664 as I had experienced a number of lock-ups after going from the 386 jernal to the 686 version (but things seemed much snappier). I think I will take upgrades much slower and more deliberatly this time - especially since this laptop is my primary work machine. Sometimes I miss the "just works" experience of my Mac. I dont recall having these probs with Debian (sid i think) either (on other machines) but I am very much encouraged by the ubuntu community here.

---

### Post by alastair on 2005-07-09
I have a centrino laptop but have stuck to the 386 kernel. If it ain't broke ...

Anyway, works fine. Perhaps I might try the 686 kernel sometime - but only if I can be bothered and am prepared to fix things that break.

I just use the official repositories.

---

### Post by secundar on 2005-07-09
[QUOTE=alastair]If it ain't broke ...[/QUOTE]

Words my laptop can live by.

After a late night things are pretty much back to the lovely state they were in before i mucked it up. 386 kernel + ubuntu Nvidia drivers/glx... I did add backports to Repositories but I'll be careful - i promise.

I've also got sound back buy building the ALSA stuff (v1.09) using [https://wiki.ubuntu.com//HdaIntelSoundHowto](https://wiki.ubuntu.com//HdaIntelSoundHowto).

---

