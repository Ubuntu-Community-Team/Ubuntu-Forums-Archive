---
title: "GRUB went messy after attempting a triple-boot system"
date: 2008-12-14
forum: General Help
---

### Post by Crana on 2008-12-14
After spending all day figuring Ubuntu out all over again I've come across a problem.  I started off with only Vista installed, then I installed Windows XP Pro and finally Ubuntu.  My problem is that GRUB incorrectly labels Vista and as a result it loads up Windows XP when I select the Longhorn option.  Any ideas?

---

### Post by caljohnsmith on 2008-12-14
OK, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And then you can modify the "title" line for Vista to instead be XP.

---

### Post by Crana on 2008-12-15
Oh, I forgot to mention I can't access Vista at all either... as well as Ubuntu shows up twice in the main menu (Generic lin.., recovery.. etc).

Currently this is what my GRUB looks like (minus the comments):

```

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		8fc1221d-8be4-40e9-8bd4-5624ad323ae8
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8fc1221d-8be4-40e9-8bd4-5624ad323ae8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		8fc1221d-8be4-40e9-8bd4-5624ad323ae8
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8fc1221d-8be4-40e9-8bd4-5624ad323ae8 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8fc1221d-8be4-40e9-8bd4-5624ad323ae8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8fc1221d-8be4-40e9-8bd4-5624ad323ae8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8fc1221d-8be4-40e9-8bd4-5624ad323ae8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8fc1221d-8be4-40e9-8bd4-5624ad323ae8 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8fc1221d-8be4-40e9-8bd4-5624ad323ae8
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Oh, and while I'm at it, is it possible to change the default choice to Vista?  :)

---

### Post by caljohnsmith on 2008-12-15
OK, I'll need some more info, so how about downloading the attached "boot_info7.sh.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info7.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please attach that to your next post, or simply copy/paste the contents to your next post. That will greatly clarify your setup and what your problem might be.

---

### Post by Crana on 2008-12-15
Handy tool you have there :D  I attached the output file, cheers.

EDIT: oh and I took a screenshot of GParted, incase it helps:

[http://i33.tinypic.com/2po9svr.png](http://i33.tinypic.com/2po9svr.png)

---

### Post by caljohnsmith on 2008-12-15
I agree, I like that script a lot too; forum member Meierfra is the one who authored it and deserves all the credit. :) 

Unfortunately it looks like part of your problem is you installed XP on top of your Vista sda1 partition, so now you have XP with at least some remnants of Vista left in that partition; but how much of Vista is left I don't know at this point. I think you might have meant to install XP to sda5, your logical partition. If you had done that, Windows XP would have put its boot files in your sda1 Vista partition, but XP would not have taken over the Vista partition as it currently looks like.

---

### Post by Crana on 2008-12-15
Well, after looking in the Vista partition all files are intact, and yeah, the partitions got really messy so I guess I made that mistake :(

How do I go about correcting it?  I was thinking about using Vista's own recovery tool.

---

### Post by caljohnsmith on 2008-12-15
> **Crana said:**
> Well, after looking in the Vista partition all files are intact, and yeah, the partitions got really messy so I guess I made that mistake :(

How do I go about correcting it?  I was thinking about using Vista's own recovery tool.
You're right, you could try doing a "Vista Repair" from the Vista Install CD, and that might at least get you Vista back. But then if you install XP to sda5, XP will take over the booting process since it will put its boot files in Vista's partition; then you won't be able to boot Vista. If you want both XP and Vista on that drive, I would first try installing XP to your sda5 partition, and if that is successful, you could run the Vista Repair option to try and get Vista back. Or if the Vista Repair is not enough to salvage Vista, you could reinstall Vista to sda1, and that should be OK since Vista should recognize XP on the drive and add XP to its boot loader. In other words, the main thing is installing Vista after XP, and not the other way around in order to be able to boot both Vista and XP. Good luck and let me know how it goes. :)

---

### Post by caljohnsmith on 2008-12-15
I take back what I said in my previous post; I just received word from meierfra (the author of that script you ran) that it is likely that the results for XP and Vista weren't quite accurate in your case. That means you may all ready have XP installed OK into sda5, and there is no need to reinstall either Vista or XP; you will just need to do a little work to separate them, since XP put its boot files in Vista's partition and also modified the Vista boot sector. How about posting the output of the following commands:
```
sudo mkdir /mnt/sda1 /mnt/sda5
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda5 /mnt/sda5
sudo mv /mnt/sda1/boot.ini /mnt/sda1/ntldr /mnt/sda1/NTDETECT.COM /mnt/sda5
```
And then the next thing you will need to do is repair Vista's boot sector, so if you have your Vista Install CD, boot that, go to the command line, and run:
```
bootrec /fixboot
```
And then you should be able to boot Vista from your Grub menu if all goes well. How about giving the above method a shot and let me know how it goes.

---

### Post by Crana on 2008-12-15
Good news: I ran the repair tool via the Vista install disk and now I have access to Vista :) Bad news:  I tried to use a tool called "EasyBCD" and as a result I've lost access to Ubuntu and XP now :(

I'll try your latest method once I get GRUB sorted out :p

---

### Post by caljohnsmith on 2008-12-15
OK, if you would like a little help reinstalling Grub to your HDD's MBR (Master Boot Record), how about doing:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Please post the output, reboot, and let me know if you get your Grub menu again.

---

