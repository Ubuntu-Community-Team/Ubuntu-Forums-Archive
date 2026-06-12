---
title: "/dev/sr0 problem on USB"
date: 2009-12-03
forum: Development CD/DVD Image Testing
---

### Post by zwygart on 2009-12-03
Hi every body,

I install liveCD on USB by copying the content and booting from GRUB.


Jaunty worked well,
I installed Karmic alpha, beta and stable release, all of them made a error during boot about /dev/sr0 being not present
Recently I had to reinstall Jaunty, now he drops me at a shell after a long wait time during boot.

Also I tried out Lucid, it make the same thing as karmic, this is probably a bug, how to fix it? or will it be fixed?

Thanks for help

---

### Post by gibbylinks on 2009-12-17
I get same error on Lucid Daily Live when making USB with


[LIST]
[*]USB Startup Disk Creator
[*]Create DELL recovery media
[*]Unetbootin
[/LIST]
All the above packages give me this same error when using them and the ISO to create a live USB.

---

### Post by gibbylinks on 2009-12-19
No one any ideas. I want to test Lucid. 

I tried it before the alpha with no problems but since the alpha I can't boot. I've tried several "daily's" with this same error each time:confused:

To clarify I am getting the following error when booting from the USB stick

/init: line 7: can't open /dev/sr0: No medium found

Doesn't seem to matter how write to the stick as above post

---

### Post by Gina on 2009-12-20
> **gibbylinks said:**
> To clarify I am getting the following error when booting from the USB stick

/init: line 7: can't open /dev/sr0: No medium found

Doesn't seem to matter how write to the stick as above postI'm getting the same.  AMD64 machine.

---

### Post by gibbylinks on 2009-12-24
Still same problem on latest daily

---

### Post by dino99 on 2009-12-27
have you sent a bug report ? can't find one.

what return: fdisk with your usb device; how have you format it (which OS, which settings)

---

### Post by sparker256 on 2009-12-27
> **gibbylinks said:**
> No one any ideas. I want to test Lucid. 

I tried it before the alpha with no problems but since the alpha I can't boot. I've tried several "daily's" with this same error each time:confused:

To clarify I am getting the following error when booting from the USB stick

/init: line 7: can't open /dev/sr0: No medium found

Doesn't seem to matter how write to the stick as above post

I have just booted using my usb thumb drive with todays daily build made with USB Startup Disk Creator. I get the same errors you are seeing but it still boots. I am running nvidia so I get a dialog box to that it must be run in low res. After answering that I get a login box that you cannot find the right password for. I found this in the Lucid Lynx Testing and Discussion forum.

I waited until the login screen appeared, then switched using "ctrl+alt+f1" to a new screen.
after that it was

```

sudo useradd -d /home/username -m username
sudo passwd username
sudo adduser username admin

```

I switched back to "ctrl+alt+f8" and was able to login and start the installer program which is under "system->administration"

What I did find is that because it is a thumb drive if you reboot after that it will take you the login screen and all you have to do then is enter your password.

Hope this helps Bill

---

### Post by gibbylinks on 2009-12-27
> **dino99 said:**
> have you sent a bug report ? can't find one.

what return: fdisk with your usb device; how have you format it (which OS, which settings)

Bug report submitted. [https://bugs.launchpad.net/ubuntu/+bug/500822](https://bugs.launchpad.net/ubuntu/+bug/500822)

---

### Post by SigiSi on 2009-12-28
> **gibbylinks said:**
> Bug report submitted. [https://bugs.launchpad.net/ubuntu/+bug/500822](https://bugs.launchpad.net/ubuntu/+bug/500822)Disable floppy or. floppy controler in BIOS (if you don't have a floppy drive).

---

### Post by harold1 on 2009-12-28
How do you disable floppys. Can that be done with a program in the gui?

---

### Post by gibbylinks on 2009-12-29
> **harold1 said:**
> How do you disable floppy's. Can that be done with a program in the GUI?

> Disable floppy or. floppy controller in_** BIOS**_ (if you don't have a floppy drive). **BIOS** (Basic Input Output System - showing off now) is a small built-in program your PC runs when you boot it up.  Normally you hold down a specific F-key on boot up to enter the BIOS. Although it can vary from manufacturer to manufacturer.

It's not a great idea to mess around in the BIOS unless you know what your doing.

---

### Post by Sagir on 2009-12-29
Hi,

I think I have the same problem.
I booted Ubuntu from a 9.10 disk (the normal version from the ubuntu website).

From there I installed a Ubuntu system on a USB stick.

Started my via epia system from that stick. Everything worked kind of ok, but from time to time firefox and other application frooze and the machine did not respond anymore.

To solve those crash situations, I then installed all packages and patches, that were offered in the package manager.
After everything had been installed, I did a reboot ....

From now on the sytem could not start properly and I receive the /dev/sr0 error message.

Sagir

---

### Post by amsterdamharu on 2010-01-29
[solved]
Reformatted the usb disk, used latest unetbootin and created usb, now it works without any errors that I can see.


I have the same problem here but after the can't open /dev/sr0 error it drops to busybox shell and nothing happens after that.

The error is initramfs unable to find medium containing live file system.

When I type mount I see the usb drive is not mounted (no wonder there is no medium containing live cd ). I think I might be missing some kernel parameters at the boot menu, here is my boot menu entry for the live cd:

```
label ubuntu
menu label Ubuntu live
kernel /casper/vmlinuz
append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

```Will now try without quiet and splash option but I don't see (of find any using google) option to tell it to run from usb instead of cd/dvd. Is there a list out there somewhere with valid kernel parameters? Can anyone who has this working post the entry in their syslinux.cfg?

---

### Post by novebeta on 2010-02-17
try to remove this option
 ```
file=/cdrom/preseed/ubuntu.seed
```and add this option 
```
live-media-path=/casper/
```and add this option (to prevent the boot from hanging with infinite "stdin: error 0" outputs)
```
ignore_uuid
```full sample
```

kernel /casper/vmlinuz
append boot=casper initrd=/casper/initrd.lz live-media-path=/casper/ quiet splash ignore_uuid --

```this work for me...

---

### Post by yopensource on 2010-05-12
> **novebeta said:**
> try to remove this option
 ```
file=/cdrom/preseed/ubuntu.seed
```and add this option 
```
live-media-path=/casper/
```and add this option (to prevent the boot from hanging with infinite "stdin: error 0" outputs)
```
ignore_uuid
```full sample
```

kernel /casper/vmlinuz
append boot=casper initrd=/casper/initrd.lz live-media-path=/casper/ quiet splash ignore_uuid --

```this work for me...

It work for me too. :guitar:
Thank you very much.

---

### Post by vaze on 2010-05-23
> **novebeta said:**
> try to remove this option
 ```
file=/cdrom/preseed/ubuntu.seed
```and add this option 
```
live-media-path=/casper/
```and add this option (to prevent the boot from hanging with infinite "stdin: error 0" outputs)
```
ignore_uuid
```full sample
```

kernel /casper/vmlinuz
append boot=casper initrd=/casper/initrd.lz live-media-path=/casper/ quiet splash ignore_uuid --

```this work for me...
Excuse me, but i'm quite a noob. Where do i modify these parameters?

Thanks!

---

### Post by timur_ba on 2010-06-01
Normally in syslinux.cfg file, as written above, if it's simple USB with just Ubuntu. 
In some other case, it's menu.lst with multiple entries and boot options.

---

### Post by Boslow on 2010-06-01
> **SigiSi said:**
> Disable floppy or. floppy controler in BIOS (if you don't have a floppy drive).


Many Many Thanks. This worked for me straight away. The USB stick worked on many other computers but this one had no floppy in it. Got to the installer fine now 

Cheers!!!
Boslow

---

### Post by LinuxBimmer on 2010-06-05
> **SigiSi said:**
> Disable floppy or. floppy controler in BIOS (if you don't have a floppy drive).

I had the same problem installing ubuntu 10.04 64bit and mythbuntu 10.04. This worked for me. THANKS!

---

### Post by toggles on 2010-07-18
> **SigiSi said:**
> Disable floppy or. floppy controler in BIOS (if you don't have a floppy drive).

Many many thanks, this worked for me too.

---

### Post by SuporteTecnicoID on 2010-07-24
Originally Posted by SigiSi  View Post
Disable floppy or. floppy controler in BIOS (if you don't have a floppy drive).


Tks,,,,Obrigado,,,,,,realmente foi só desabilitar o Floppy na BIOS e tudo rodou lindo e maravilhoso, no Linux KDuXPv1.98......disponha quando precisar também........


atenciosamente.....

SuporteTecnicoID

---

### Post by kingdom529 on 2010-08-03
> **SigiSi said:**
> Disable floppy or. floppy controler in BIOS (if you don't have a floppy drive).

Worked for me as well. Many Thanks!

---

### Post by rmsx97 on 2010-11-17
I'm getting this error as well with Ubuntu 10.10.

I used UNetbootin to create the USB install (since the one that comes in the 10.10 iso image doesn't work - you select the .iso and it won't show up in the list), and during the init it just sits in a "can't open /dev/sr0" loop. Eventually it leads to the "unable to find a medium containing a live file system"

I don't have an option to disable a floppy in my BIOS. I'm using a newer Dell laptop with i7.

Is there a real workaround for this other than disabling the floppy in the BIOS? I've read a ton of other threads on this very problem, and most are saying it's a casper init issue. 

Another pointed me to editing the loopback.cfg in grub to point to the actual iso file, so I have "iso-scan/filename=/ubuntu.iso", but still no go.

I'd try an actual install disc but don't have any blanks on me... figured the USB install would be just fine.

---

### Post by Pilot824 on 2011-03-05
My laptop, I can safely say is "Special". I received my HP Pavillion DV9000 first with Vista on it, after 3 years of torture I installed Linux Mint onto it. Was awesome, no probs till about 1/2 a year in or so. Linux Mint died, all I remember was that the error had to do with a Kernel. Anyways, so later on I install Ubuntu. Again, was working fine for several months until it started to get glitchy. Every so often, it would not boot and give me a random error message every time, but then on other boots it would work. So now I am at the point where my laptop completely died, and I messed it up because my friends dont know how to give me the DESKTOP version of Ubuntu and not the Server -_-.

Anyways, I am currently at somewhat of a similar spot as everyone who has read the forum this far: Ubuntu wont get past its boot logo, and the code its giving me (for some reason, it displays some sort of log when I press my 'mute' key) is:
```
Killed
stdin: error 0
/init: line 7: can't open /dev/sr0: No medium found
/init: line 7: can't open /dev/sr0: No medium found
unable to open '/dev/sda'
```

and it repeats, a new chunk of the above code every time I re-enter into the log thing.

I tried fixing it by editing the boot code, and disabling the floppy boot option.

Any other idea's?

---

### Post by senthil2302 on 2011-07-29
I had same problem, after that i found that i am connected with usb 3 port(blue ), after changed the norma usb port it worked form me.

---

### Post by Matifou on 2011-08-21
Hi

Relaunching the topic... I have exactly the same issue with Ubuntu 11.4 and Casper. 

Sol A grub options: just appending it doe snot work... seems that it is not working for persistent version :-( At once could boot but mouse did not move... see:
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/492301](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/492301)

SOL B, BIOS: did not find how to disable floppy on BIOS of Dell Latitutd E6400...

Any idea?

Thanks!!

---

### Post by Tuexnovia on 2013-03-12
> **novebeta said:**
> try to remove this option
 ```
file=/cdrom/preseed/ubuntu.seed
```and add this option 
```
live-media-path=/casper/
```and add this option (to prevent the boot from hanging with infinite "stdin: Error 0" outputs)
```
ignore_uuid
```full sample
```

kernel /casper/vmlinuz
append boot=casper initrd=/casper/initrd.lz live-media-path=/casper/ quiet splash ignore_uuid --

```this work for me...

Well guys I'm having this problem in this post: [http://ubuntuforums.org/showthread.php?t=2124874&p=12554758#post12554758](http://ubuntuforums.org/showthread.php?t=2124874&p=12554758#post12554758)


let's see if someone else can help, let me ask you something by the way, how do you put this code in ISO file...? I've cheked this one ubuntu-12.10-desktop-amd64, and I don't know where to put it exactly...

---

### Post by SpawnHappyJake on 2013-07-13
Hi guys.

  Just thought I'd drop a note coming from Linux Mint (essentially Ubuntu), Fedora, and Archbang.

  For booting into a Live Mint environment off USB, my problem was that I was being too impatient. I thought it was broke, but actually needed about a minute and a second to boot.

  Try adding ```
cdrom-detect/try-usb=true
``` as a kernel boot parameter. It makes it wait for USB devices to be noticed if no CD drive is found. Should help with > /init: line 7: can't open /dev/sr0: No medium found

I did not need "live-media-path" and did not need to remove "file=...". It didn't even *need* "cdrom-detect/try-usb=true" in my case, but, in general, I think the parameter helps for booting live USB environments.


For Fedora's installer I do:

```
linux /boot/vmlinuz-3.1.0-7.fc16.x86_64 root=UUID=[UUID of filesystem on USB drive] rootfstype=auto ro liveimg quiet  rhgb rd.luks=0 rd.md=0 rd.dm=0
initrd /LiveOS/initrd0.img
```

And for Archbang's installer I do:
```
linux /arch/boot/x86_64/vmlinuz archisobasedir=arch archisolabel=ArchBang64
initrd /arch/boot/x86_64/archiso.img
```

Hope that helps,
Jake

---

