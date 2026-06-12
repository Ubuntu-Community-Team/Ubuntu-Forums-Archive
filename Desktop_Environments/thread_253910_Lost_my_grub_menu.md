---
title: "Lost my grub menu"
date: 2006-09-09
forum: Desktop Environments
---

### Post by watto_one on 2006-09-09
I reformatted a partision that had Kubuntu on it ( not my primary partitision I'm running Ubuntu on hda1. When I rebooted I have lost my grub menu.
Error 15 message. 
As you can probably guess I'm not very cluey with Ubuntu or computers in general so I wood apreciate step by step help on how to reinstall the grub menu so I can get my Ubuntu to boot again.
It is not a duel boot machine just Ubuntu
Thanks in advance

Edit:  I found Catlet's How Do and have bee able to repair it. Thanks to all who looked at my problem

---

### Post by Herman on 2006-09-09
Hello, watto_one,
Download a copy of [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") , in my opinion, this one is the best version so far,                    [             sgd_0.9462.iso.bz2. ]("http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=82") Burn that to a CD-RW or a CD-R disk.

To boot Ubuntu with Super Grub Disk, boot with the disk in your CD Drive (of course, where else? :D ), and select 'English Super Grub Disk', then -->Restore Grub in Hard Disk (MBR) -->Automatically Install.

The reboot and remove the Super Grub Disk to make sure it worked.

And you should be good to go!
Here's the Super Grub Disk documentation page, just in case you need to refer to it, [Click Here.]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

Any problems, please don't be shy to ask,

Regards, Herman :D

---

### Post by Phasmagon on 2006-09-09
I guess that is one way to go, but I would think that there is much easier than that.

Boot up your computer.

When your you get the grub error press c for a command line

then type

```
root (hd0,0)
kernel /boot/*vmlinuz* root=/dev/hda1
initrd /boot/*initrd*
boot
```

Note you should select a specific kernel image. So when type vmlinuz press Tab to autocomplete the image filename. If you have more than one kernels installed, Tab will display a list of available kernels. If so, you should continue typing the filename of the kernel with the highest number.

The same goes for initrd.

This should boot your computer into Ununtu.

When you finally get into ubuntu. Open a terminal and type

```
sudo grub-install /dev/hda1
```

And that is that. Although it seems that Hermans solution is easier I disagree. The solution I am refering to takes approx. 3 mins and does not require booting into another computer/OS or live-CD and does not need any external resources. And secondly, it helps understanding a little bit more your computer.

The choise though is yours. :)

---

### Post by wouterd on 2006-09-09
> **Phasmagon said:**
> 

When you finally get into ubuntu. Open a terminal and type

```
sudo grub-install /dev/hda1
```

And that is that. ...



shouldn't that be 

```
sudo grub-install /dev/**hda0**
```

---

### Post by Azathoth_ on 2006-09-09
This sould be
```
grub-install /dev/hda
or
grub-install /dev/sda (if you use a serial ata on the master
```
You do not have to put the number

---

### Post by watto_one on 2006-09-09
Thank you all for the help. I will keep this post so that when I do something stupid next time, fixing it will be alot less of a worry.:D

---

