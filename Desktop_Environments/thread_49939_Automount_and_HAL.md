---
title: "Automount and HAL"
date: 2005-07-18
forum: Desktop Environments
---

### Post by scorcher on 2005-07-18
A while back my Hoary desktop stopped automounting anything.

I fixed it by using System -> Administration -> Users and Groups setting the the user privileges for user 'hal' to 'Access to CD-ROM Devices', 'Access to Floppy Devices' etc.

Now if I run 'groups hal' it says: "hal : hal cdrom floppy tape audio plugdev scanner"

Should 'hal' be a member of these groups?

Also, does anyone know what groups 'hal' should be member of for everything to work properly?

---

### Post by scorcher on 2005-07-31
Could someone please post the output of
```
groups hal
```
Thank you!

---

### Post by BillH on 2005-07-31
[QUOTE=scorcher]Could someone please post the output of
```
groups hal
```
Thank you![/QUOTE]

hal : hal cdrom floppy plugdev

---

### Post by scorcher on 2005-07-31
[QUOTE=BillH]hal : hal cdrom floppy plugdev[/QUOTE]
Thanks.

---

### Post by RevNomad on 2005-08-03
Did this correct your automount problem?  I'm having the same issue with USBkeys.  Also does the system need to reboot for the changes to take affect?

Norman

---

### Post by scorcher on 2005-08-03
[QUOTE=RevNomad]Did this correct your automount problem?  I'm having the same issue with USBkeys.  Also does the system need to reboot for the changes to take affect?

Norman[/QUOTE]
Yes, adding hal to the 'cdrom floppy plugdev' groups did fix automounting for me.

I can't remember if I had to reboot the computer or just logout and back in again.

I would reboot the computer anyway just to be safe.

---

### Post by snafoo on 2005-08-03
On my system the user hal is member of the groups cdrom, floppy, and plugdev, but I am still having automount problems.

CDs and DVDs won't get mounted automatically when I insert them.

---

### Post by RevNomad on 2005-08-03
Yea!  It worked.  

Thanks
NTP

---

### Post by der_joachim on 2005-08-03
> I would reboot the computer anyway just to be safe.

IIRC, you just have to restart the HAL service. What I don't RC, is the name of the service (too much blood in my caffeine) ](*,) . Just do a ```
sudo /etc/init.d/<service_name> restart
``` and it should work again. Disclaimer: it's been a while since I had to configure an automnounter, thanks to the Ubuntu team. :)

---

### Post by scorcher on 2005-08-03
[QUOTE=der_joachim]IIRC, you just have to restart the HAL service.[/QUOTE]
You're right just restarting the service should work.
The service is dbus-1. So just run 
```
sudo /etc/init.d/dbus-1 restart
```

---

### Post by scorcher on 2005-08-03
[QUOTE=snafoo]On my system the user hal is member of the groups cdrom, floppy, and plugdev, but I am still having automount problems.

CDs and DVDs won't get mounted automatically when I insert them.[/QUOTE]
Check if automounting enabled.
Goto 'System -> Preferences -> Removable Drives and Media' and see if there is a check by 'Mount removable media when insterted'

---

### Post by snafoo on 2005-08-03
Automounting is enabled in the menu.

I realized a strange behaviour: At the moment I'm using the kernel image 2.6.10-5-k7. For testing I upgraded to the 2.6.11 image from the Ubuntu repository. I switched back, because I got some strange system crashed every once in a while. The system just freezed and I don't know how to reproduce it. But the automounting worked with that kernel.

I am confused...

---

### Post by twowheeler on 2005-08-04
It may be a kernel config problem.  See this [post](http://ubuntuforums.org/showthread.php?t=37488) for a suggestion.   I thought about upgrading to a 2.6.11 kernel but having seen your post I am glad I didn't.

---

### Post by twowheeler on 2005-08-04
Here's something else that may be helpful.  There is a very thorough debugging guide [here](http://qa.mandrivalinux.com/twiki/bin/view/Main/HotPluggableHardwareRemovableMedia)  at the mandriva site.  Step by step instructions on how to tell what is wrong with hal, dbus, etc.

---

### Post by littlepr on 2005-08-10
Problems with automount here. It was working until yesterday. WinXP can mount and read this drive but ubuntu can't.

Here is a log:

Aug 10 19:39:02 localhost kernel: usbcore: registered new driver usb-storage
Aug 10 19:39:02 localhost kernel: USB Mass Storage support registered.
Aug 10 19:39:02 localhost usb.agent[8393]:      usb-storage: loaded successfully
Aug 10 19:39:07 localhost kernel:   Vendor: GS-Magic  Model: stor 1040A        Rev: 4g28
Aug 10 19:39:07 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Aug 10 19:39:07 localhost kernel: SCSI device sda: 7999488 512-byte hdwr sectors (4096 MB)
Aug 10 19:39:07 localhost kernel: SCSI device sda: 7999488 512-byte hdwr sectors (4096 MB)
Aug 10 19:39:08 localhost scsi.agent[8485]:      sd_mod: loaded sucessfully
Aug 10 19:39:08 localhost kernel:  /dev/scsi/host0/bus0/target0/lun0: p1
Aug 10 19:39:08 localhost kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
tail: cannot open `output::' for reading: No such file or directory

---

### Post by giopas on 2005-08-18
Hi!  :D

This is my first post, and I would primary thank everyone who work and worked for this excellent distro! :D

I've got the same "automount" problem a lot of people found here during these months, and it's driving me crazy!  ](*,)

In short:
yesterday (just after I've installed samba) I discovered that my external hard drive, my usbpens and my cd-rom didn't automatically mount at boot. That's sounded really strange for me at the beginning, because I didn't remove any other applications, but after I'd taken a look at this forum, I discovered that is quite a common problem.

So according to other users' suggests, I've already checked if gnome-volume-manager works, and it does; I've upgraded from Debian testing repository the "libsysfs" library, but nothing seems changed; I checked if in gnome-volume-preferences everything is fine.. and it look like that!

So, what's wrong?

I've also read from [here](http://ubuntuforums.org/showthread.php?t=37488) that could be a kernel upgrading problem, but I didn't try to downgrade: I'm still too newbie to do it. :D

What is the solution? Please help me!

thnx to everyone!

enjoy, ;)
giopas

---

### Post by scorcher on 2005-08-22
> **giopas]Hi!  :D

This is my first post, and I would primary thank everyone who work and worked for this excellent distro! :D

I've got the same "automount" problem a lot of people found here during these months, and it's driving me crazy!  ](*,)

In short:
yesterday (just after I've installed samba) I discovered that my external hard drive, my usbpens and my cd-rom didn't automatically mount at boot. That's sounded really strange for me at the beginning, because I didn't remove any other applications, but after I'd taken a look at this forum, I discovered that is quite a common problem.

So according to other users' suggests, I've already checked if gnome-volume-manager works, and it does said:**
> here[/URL] that could be a kernel upgrading problem, but I didn't try to downgrade: I'm still too newbie to do it. :D

What is the solution? Please help me!

thnx to everyone!

enjoy, ;)
giopas

Run Applications -> System Tools -> Terminal
type
```
groups hal
```
And post the output here.

---

### Post by theraginasian on 2005-08-28
[QUOTE=scorcher]Yes, adding hal to the 'cdrom floppy plugdev' groups did fix automounting for me.

I can't remember if I had to reboot the computer or just logout and back in again.

I would reboot the computer anyway just to be safe.[/QUOTE]

Yes, thank you very much this worked for me as well!

---

### Post by flamarro on 2005-08-29
[QUOTE=scorcher]Run Applications -> System Tools -> Terminal
type
```
groups hal
```
And post the output here.[/QUOTE]

I've been reading this thread and i have the same problem related here. I did what you've asked. Result:

```
hal : hal cdrom floppy plugdev
```

---

### Post by nianhbg on 2005-12-17
Hello 

I also had some problems with my usb discs i am running hoary. 
And i did some changes i group hal. And all works now thanks :)

---

### Post by coaxx on 2006-02-02
[QUOTE=twowheeler]Here's something else that may be helpful.  There is a very thorough debugging guide [here](http://qa.mandrivalinux.com/twiki/bin/view/Main/HotPluggableHardwareRemovableMedia)  at the mandriva site.  Step by step instructions on how to tell what is wrong with hal, dbus, etc.[/QUOTE]

thx!

---

### Post by rgs1945 on 2006-02-27
I have Breezy with the Gnome desktop on an IBM laptop.

After following various guides and how-tos on getting my floppy to mount when a diskette is inserted and unmount when it is removed, and experimenting with pmount, autofs, fstab,hal, groups and various other stuff - it still don't work. I'm probably missing something obvious. 

Does anyone know of a step-by-step procedure to use on a fresh install of Breezy, to achieve this ?

---

### Post by K.Mandla on 2006-03-04
Just a note: I had this same problem with a clean Breezy install on a Dell Inspiron 600m. Automount stopped working for some reason, for an NEC DVD+/-RW drive. The machine is a dual boot, and Windows could access it fine.

Hal did not have permission to access floppies or CDs in my case, and restoring that privilege fixed the automount issue. I rebooted Ubuntu after tweaking that, just because I have a hard time getting used to the fact that I don't need to reboot all the time. Call it a comfort issue. :) 

Thanks, all.

---

### Post by stanz on 2006-03-07
Hi All...
I've just got the "failed to initialize HAL" error messegs, and had another from my floppy, not mounting(don't recall it).
I've followed all your advices..with some problems with:
**:~$ sudo /etc/init.d/dbus-1 restart **code, not working till changed to:
--------------------
[B]:~$ sudo /etc/init.d/dbus restart
 * Stopping Hardware abstraction layer:                                  [ ok ]
 * Stopping system message bus...                                        [ ok ]
 * Starting system message bus...                                        [ ok ]
 * Starting Hardware abstraction layer:                                  [ ok ]
[/B]--------------------
With that output- i haven't logged out yet.
I'd ask- How to check, on the 'permissions' issue...if someone would share?
HAL is in the required 'groups' for me.

---

### Post by xinelo on 2006-08-08
> **K.Mandla said:**
> Hal did not have permission to access floppies or CDs in my case, and restoring that privilege fixed the automount issue.

Hi, 

Could you explain in more detail how you restored those permissions? Thanks
xinelo

---

