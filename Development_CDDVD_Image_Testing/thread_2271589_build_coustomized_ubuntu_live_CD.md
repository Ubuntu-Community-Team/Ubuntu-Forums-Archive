---
title: "build coustomized ubuntu live CD"
date: 2015-03-31
forum: Development CD/DVD Image Testing
---

### Post by emmebi75 on 2015-03-31
Hi,
I’m trying to create a customized version of the Ubuntu 14.04 LIVE CD, using the live-build scripts  as follows :
   [FONT=lucida console]lb config --archive-areas "main universe" --distribution "trusty" --mode "ubuntu"
  lb build[/FONT]
This produces a live iso image that does not boot, I receive the following error: 
[FONT=lucida console]  /casper/vmlinuz : file not found[/FONT]
 
If I force GRUB as boot loader, as follows:
   [FONT=lucida console]lb config --archive-areas "main universe" --distribution "trusty" --mode "ubuntu" –botloader “grub”
  lb build[/FONT]
the build step does not complete, it stops with the following error:
[FONT=lucida console]  E: Package 'grub-legacy' has no installation candidate[/FONT]
 
Can anyone help me?
Thanks a lot!

---

### Post by bardo2 on 2015-04-01
No, i cannot. Just recalling, that Ubuntu Live-CD/DVD are quite unique (compared to other distros), since you can boot from those images even directly using grub2. So i would guess, there is nothing obviously easy, as even debian doesnt get that feature to work. Doesnt that error message hint you forward? Ubuntu-ISO's contain a subdirectory casper with the kernel and initram images inside. So i guess you need one too.

---

### Post by sudodus on 2015-04-01
Welcome to the Ubuntu Forums :-)

It is a rather advanced task to create an iso file, that works to run Ubuntu live and to install Ubuntu. You can try with Remastersys or some fork of it.

But there are other methods. If it is not necessary to make an iso file, but you want to make a portable system, that can be run in 'any' computer from a USB pendrive or installed into other computers, you can make an OEM installed system. If you avoid proprietary drivers, it is portable between most computers. (You might have to install a proprietary driver for graphics or wifi, if you have certain chips for graphics or wifi.)

See these links

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=2172971"]
One Button Installer, 'OBI'[/URL]

---

### Post by QDR06VV9 on 2015-05-16
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

It is a rather advanced task to create an iso file, that works to run Ubuntu live and to install Ubuntu. You can try with Remastersys or some fork of it.

But there are other methods. If it is not necessary to make an iso file, but you want to make a portable system, that can be run in 'any' computer from a USB pendrive or installed into other computers, you can make an OEM installed system. If you avoid proprietary drivers, it is portable between most computers. (You might have to install a proprietary driver for graphics or wifi, if you have certain chips for graphics or wifi.)

See these links

[One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971")
Thank You sudodus!
Been using Linux for over 10 years now and this is first I have heard of 9w.
Sorry for off topic, but greatful.
Regards

---

### Post by sudodus on 2015-05-16
You are welcome :-)

You might be interested in [ToriOS]("http://torios.net/") - now at beta stage - which uses the OBI in a way, that is developed from the 9w installer.

---

