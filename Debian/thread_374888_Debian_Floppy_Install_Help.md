---
title: "Debian Floppy Install Help"
date: 2007-03-03
forum: Debian
---

### Post by VoodooSteve on 2007-03-03
I was given this ancient laptop (Pentium 100MHz, 40MB RAM, 800MB Hard Drive) and even though I can think of very little use of it, I would still like to have an OS other than Windows 95 on it. Debian has a text-only option which I think would run well on this machine. When I boot up to the floppy, I see the Debian logo and the boot: prompt and I hit enter and linux and initrd.gz load. However, when done, the system reboots and the whole process repeats itself. I tried a different floppy and the same thing occurred. Any ideas to the cause of this problem? Or perhaps there in another distro that might work as well?

---

### Post by kerry_s on 2007-03-03
DSL-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

You can have a gui. :)

---

### Post by VoodooSteve on 2007-03-03
Unfortunately, this laptop has no cdrom drive and from what I've read, DSL requires one to install the OS. It sucks because it really limits my options, but I really don't want to spend any money on it.:-P

---

### Post by Rodneyck on 2007-03-03
I found this..

[http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_with_Netcard_(Poormans_Install)](http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_with_Netcard_(Poormans_Install))

---

### Post by mips on 2007-03-05
If the laptop has a ethernet/network connection you could do a network install of debian.

---

### Post by dimeotane on 2007-04-26
I'm working on a similar project, to recycle old pentium laptops with linux.  I found that ubuntu did a better job of detecting PCMCIA network cards than debian net install. I have about 8 different types of  3COM and megahertz cards.. none of which would work under debian net install.   It did ask for other network drivers .. which makes me wonder if I can find another one other than the two that are provided.   I tried the [goodbye-microsoft.com ]("http://goodbye-microsoft.com/")with running the debian.exe ... I got as far as grub on that.  Supposedly it installs debian etch?

This is a huge area for development and documentation.  The majority of the world's population will be introduced into the internet through low end  machines. 

Heres a list of [floppy linux distros]("http://www.linuxlinks.com/Distributions/Floppy/")
[URL="http://mulinux.dotsrc.org/download.html"]
[/URL]Mulinux is a floppy based install with X windows gui.
One reviewer writes:* I have tried MuLinux and it is totally unacceptable! It was written in 1998-1999 and has never been updated. It is very rudimentery, No wifi support, no etho support as far as I can tell all it really has is a GUI desktop (required a extra floppy) and VERY minamalistic software options. No package manager, no apt-get, no nothing. Reminds me of installing Windows 3.1 back in the day.*

Anyways, a minimal install of ubuntu may be the way to go: there's [fluxubuntu ]("http://fluxbuntu.org/")and [ubuntu-lite]("http://en.wikipedia.org/wiki/Ubuntu_Lite").  
However, this review[/URL] says that fluxubuntu needs 96mb of RAM (which seems kinda silly).
Another reviewer wrote that "I think Ubuntu requires 64mb of ram and a little more then 3 gb to install. The slowest machine I installed it on was a 400 mhz PII, 128 of ram, and 8 mb video card. It was really slow too."
Another user reports that,  "do a server install, then install ubuntu-minimal and fluxbox. You'll then have an as small as possible ubuntu system with fluxbox and without gnome."

Puppy linux and DSL linux may be the better way to go on low end /legacy machines. 

Here's some more ubuntu-lite info
[https://help.ubuntu.com/community/InstallingUbuntuLite](https://help.ubuntu.com/community/InstallingUbuntuLite)
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)
[http://packages.ubuntu.com/breezy/base/ubuntu-minimal](http://packages.ubuntu.com/breezy/base/ubuntu-minimal)
[URL="http://mrbrown.iblog.com/post/213829/324268"]

---

### Post by gigi1234 on 2007-05-08
I have a similar machine: a Gateway Solo Laptap, Pentium 1, 40 MB RAM, 1 GB HD, no CD ROM. I had the exact problem you having with trying Debian (Etch) and Ubuntu (Edgy) netinstalls using boot floppies: the process quits at initrd (loading the ramdisk). I think this is because of the LOW RAM. 

I got DSL running fabulously on this machine, but to do it I used an old parallel 100 MB zip drive I had lying around. 

First I downloaded and burned a floppy boot disk called TOMSRTBT:

[http://www.toms.net/rb/]("http://www.toms.net/rb/")

Then I booted up the old Gateway with this boot disk (with the zip drive hooked up and turned on) and fdisked 3 partitions: 100 MB FAT32 for the DSL files, 80 MB Linux swap, and the rest to EXT2 for the hard drive installation of DSL. 

Then I created a mount point for the zip drive and mounted it:

```
mount -t vfat /dev/sda4 /mnt/zip
```

Then I copied these files from my zip drive to the FAT32 partition: KNOPPIX placed in a folder called "KNOPPIX" and the contents of /boot/isolinux into a folder called "ISOLINUX". These files are found by downloading the latest DSL ISO (current.iso) and extracting it. You will also need to find the DSL boot.img file (bootfloppy.iso) and make a DSL boot floppy. Look here for bootfloppy.img and current.iso:

[http://distro.ibiblio.org/pub/linux/distributions/damnsmall/current/]("http://distro.ibiblio.org/pub/linux/distributions/damnsmall/current/")
Once the DSL were on the FAT32 partition I booted up using the DSL boot disk and these boot options:
```

boot: fromhd=/dev/hda3  lowram vga-normal
```

DSL loaded and I was able to do a hard install from the tools menu. Try looking at the DSL WIKI for more specific instructions:

[http://www.damnsmalllinux.org/wiki/index.php/Main_Page]("http://www.damnsmalllinux.org/wiki/index.php/Main_Page")

If you don't have a zip drive you might be able to boot using TOMSRTBT, which has network support, and wget the files from a remote server. 

Maybe this makes sense to someone? 

Anyway, after a lot of fooling around I really think that DSL is the best bet for such an old machine.

You might also try a netinstall of Breezy using floppies. That is my next project. 

I am no big expert but I think there is something about Etch and Edgy that won't fly on these old clunkers.

---

