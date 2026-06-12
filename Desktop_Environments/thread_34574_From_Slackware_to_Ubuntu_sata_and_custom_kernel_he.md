---
title: "From Slackware to Ubuntu: sata and custom kernel headache"
date: 2005-05-15
forum: Desktop Environments
---

### Post by Chareos on 2005-05-15
Hi all.

I'm new to Ubuntu, and I'm loving it. The way it worked on my new AMD64 (that's the most 64-bit ready distro out there, no doubt) left me amazed.

Now I'm trying to getting more.


** 1st HELP REQUEST: MAKE UBUNTU KERNEL DO WHAT I WANT **

Due to my personal aimings, I want to put /home on a sata disk. This is a problem, because on my nForce board sata gets loaded too late to be useful at /home mount time.
Is there a way to fix this ? Afaik sata works thanks to libata, so I don't really know if I can load it sooner.
I could live even with a work-around (for example, normal mounting route, then umount /home and remount it on the sata with a script), but I'd love to hear opinions about WHEN to do it (just before being asked for a password?) and HOW - remember, I know a little about Ubuntu.



** 2nd HELP REQUEST: HOW IN THE HELL KERNEL DO WORK IN UBUNTU ? **

I've seen kernel 2.6.11.1 in Synaptic (great utility, btw). Cause my chipset (nForce4) is really bleeding edge, I prefer to stay on 2.6.11 kernel in place of 2.6.10 .
Tried to install the 2.6.11-amd-k8 kernel (headers and image), but at boot time my USB keyboard don't works.

That pushed me trying to compile my own kernel.
I did it MANY MANY times on slackware and a couple in gentoo. Always successfully.
Now I'm facing a problem.
Compilation goes well.
Then, following docs and posts around here, I packaged it and installed in the debian way. All well, image created and installed, grub updated, even initrc created (DAMN, may anybody explain me what initrc is useful for ?)...

reboot... grub can't mount root.

Of course the file system is in new kernel (built in reiserfs) so it should even bother with modules...

May anyone write down a list of steps to compile/install succesfully a 2.6.11 kernel on a reiserfs root partition ? I repeat, everything around here didn't help me. There's something I'm missing.

 EDIT: is ROM FILE SYSTEM SUPPORT necessary for initrc mechanism ? If so, shall I build-in to kernel or make a module of it ?

Many, MANY thanks
for any help.

---

### Post by bigbangbigbigbang on 2005-05-15
[QUOTE=Chareos]Hi all.

** 1st HELP REQUEST: MAKE UBUNTU KERNEL DO WHAT I WANT **

Due to my personal aimings, I want to put /home on a sata disk. This is a problem, because on my nForce board sata gets loaded too late to be useful at /home mount time.
Is there a way to fix this ? Afaik sata works thanks to libata, so I don't really know if I can load it sooner.[/QUOTE]

Try to write the needed modules to the beginning of /etc/modules.
Maybe loading it with discover/hotplug is too late.
Or compile the needed drivers in the kernel. 

[QUOTE=Chareos]** 2nd HELP REQUEST: HOW IN THE HELL KERNEL DO WORK IN UBUNTU ? **

reboot... grub can't mount root.

Of course the file system is in new kernel (built in reiserfs) so it should even bother with modules...

May anyone write down a list of steps to compile/install succesfully a 2.6.11 kernel on a reiserfs root partition ? I repeat, everything around here didn't help me. There's something I'm missing.

 EDIT: is ROM FILE SYSTEM SUPPORT necessary for initrc mechanism ? If so, shall I build-in to kernel or make a module of it ?

Many, MANY thanks
for any help.[/QUOTE]

Have you compiled the 2.6.11 sources from Ubuntu or from kernel.org?
I would strongly suggest to use 2.6.11.7 or 2.6.11.8 from kernel.org; those in Ubuntu are older and have never worked for me.

If you use initrd, Ubuntu/Debian use cramfs for it. You have to compile it in the kernel, not as a module.
But quite often, if you are going to use your kernel on one machine only, it is a better idea to make a kernel that does not need initrd.
You probably know which driver you need in order to access your root.

---

### Post by Chareos on 2005-05-15
Thanks for your reply.

#1
Adding needed modules to /etc/modules seems not enough.
Maybe fstab entries are processed even before than /etc/modules. I must instruct the kernel even before... unless I think about a workaround, I think that a recompilation is in my destiny :-)



#2
Tried kernel.org 2.6.11.9
cramfs is something I didn't take care of, and maybe that's my problem. I'll take a look tomorrow.
Also tried to completely disable  ramdisk and initrd (and commented initrd entry in /boot/grub/menu.lst) but had the same problem. I've to think that maybe I'm going wrong with grub (I'm from lilo).

Tell me, If I decide not to go for initrd... I can/must disable RAM disk and initrc from kernel ?

Then, HOW should I change this entry (particularly the initrd line) ?
---------------------------------------------------------------------------------------
title		Ubuntu, kernel 2.6.11-1-amd64-k8 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.11-1-amd64-k8 root=/dev/hda1 ro console=tty0 quiet splash
initrd		/boot/initrd.img-2.6.11-1-amd64-k8
savedefault
boot
---------------------------------------------------------------------------------------


Many thanks.

---

### Post by bigbangbigbigbang on 2005-05-15
[QUOTE=Chareos]Thanks for your reply.

#1
Adding needed modules to /etc/modules seems not enough.
Maybe fstab entries are processed even before than /etc/modules. I must instruct the kernel even before... unless I think about a workaround, I think that a recompilation is in my destiny :-)
[/QUOTE]
fstab is processed after loading modules. Is it possible that some of your needed modules do not load for some reason?
Or maybe some generic module gets loaded before the right one and comes in the way. - Just a thought (I've already had smilar problems with chipset drivers)

[QUOTE=Chareos]#2
Also tried to completely disable  ramdisk and initrd (and commented initrd entry in /boot/grub/menu.lst) but had the same problem. I've to think that maybe I'm going wrong with grub (I'm from lilo).

Tell me, If I decide not to go for initrd... I can/must disable RAM disk and initrc from kernel ?
Many thanks.[/QUOTE]
Have you really included all necessary drivers? If you want a kernel without the need for initrd you have to compile in at least the chipset driver, the driver for your sata controller, IDE and SCSI support besides the filesystem driver.
If you disable ramdisk and initrd support in kernel does not really matter. You just have to delete/comment out the initrd line from menu.lst

---

### Post by metasyntax on 2005-05-15
FWIW, I have /, and /home on SATA drives on my nforce4 mobo... works perfectly fine with the default hoary (warty had problems with the nvidia driver and PCIe) install.  I also don't encourage anyone to follow the 2.6 series too closly, there have been far too many regressions from version to version (IMO and all that).

here is my /etc/modules file:

```
sd_mod
psmouse
mousedev
usbhid
ide-cd
ide-disk
ide-generic
lp
nvidia
```

---

### Post by Chareos on 2005-05-16
I've a good reason to pass to latest kernel:


NVRM: loading NVIDIA Linux x86_64 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:45:40 PST 2005
May 16 09:48:06 localhost kernel: NVRM: WARNING: Your Linux kernel has problems in its implementation of
May 16 09:48:06 localhost kernel: NVRM: the change_page_attr kernel interface.  The NVIDIA kernel
May 16 09:48:06 localhost kernel: NVRM: module will attempt to work around these problems, but
May 16 09:48:06 localhost kernel: NVRM: system stability may be affected.  It is recommended that
May 16 09:48:06 localhost kernel: NVRM: you update to a 2.6.11 or newer kernel.


Due I'm having a strange problem in cedega, I'm willing to try.
I'll recompile my kernel in a minute, then report for success or failing.

---

### Post by Chareos on 2005-05-16
That's it !
Going to 2.6.11.9 made Cedega rock-stable.



I've another problem now:

EVERY 2 reboot my system looses nvidia drivers, and I'm not able to startx until I reinstall them.
Drivers are from nvidia site because:
if I dpkg my own kernel it asks for a initrd (I can't understand WHY... everything related is disabled). Synaptic-installed nvidia drivers are not appliable to my own kernel.


Xorg log says:

(II) Initializing extension GLX
(EE) No Input driver matching `mouse'
(EE) No Input driver matching `keyboard'
(WW) No core pointer registered
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
No core keyboard
Fatal server error:
failed to initialize core devices


but it's not related to any input... reinstalling nvidia drivers let me startx immediately.

Is there a way to fix this ?

---

### Post by bigbangbigbigbang on 2005-05-16
[QUOTE=Chareos]That's it !
Going to 2.6.11.9 made Cedega rock-stable.



I've another problem now:

EVERY 2 reboot my system looses nvidia drivers, and I'm not able to startx until I reinstall them.
Drivers are from nvidia site because:
if I dpkg my own kernel it asks for a initrd (I can't understand WHY... everything related is disabled). Synaptic-installed nvidia drivers are not appliable to my own kernel.
[/QUOTE]
If you install your kernel-image...deb with dpkg it gives you a warning about initrd, but you can safely ignore it, if you compiled all your needed drivers into the kernel. The only important thing is that /boot/grub/menu.lst has no initrd line.

Maybe you do not really lose the nvidia drivers, just they do not get loaded at boottime. Have you added the nvidia kernel modules to /etc/modules?

---

### Post by Chareos on 2005-05-17
I just checked... when x fails to start the nvidia module has been loaded anyway.

I suspect about a "creating nvidia tls links..." which I think is particular to Ubuntu (never seen in slackware or gentoo).


Note: I left installed Ubuntu nVidia drivers. Maybe I'm supposed do remove 'em to get fully working mine installed ?
Anyway Now I'll try the dpkg way.
I'd love to manage nvidia drivers for my custom kernel from Synaptic, in the end...

---

### Post by Chareos on 2005-05-17
answering to myself: no, removing Ubuntu nvidia drivers makes no differences.

---

