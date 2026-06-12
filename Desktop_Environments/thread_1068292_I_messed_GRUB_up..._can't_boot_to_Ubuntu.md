---
title: "I messed GRUB up... can't boot to Ubuntu"
date: 2009-02-12
forum: Desktop Environments
---

### Post by momitty on 2009-02-12
I am pretty much a noob at this stuff but I had installed the Startup Manager package from within Gnome.  I was tired of it keeping 18 versions of the past kernels, mostly because it kept throwing booting order off and loading into the Memtest whenever a new kernel showed up (I normally default to Windows).  So I changed the previous kernels to '0'... which is kind of misleading because I thought it truly meant previous kernels...but it really means *all* kernels.  So now my only options in Grub are memtest and Other/Windows.  No Ubuntu options are there!

I see from grub there is a command line but nothing really makes sense there.  Does somebody know how to recover it from there?  Or is there a way to boot from the CD again and then fix it?  

Thanks!

EDIT:  I tried using the Super Grub CD and I can find a file called menu.lst.backup which has the old kernels before the last update a few days ago, and then one called menu.lst~ which has everything, but if i select any options I get "Error 13 - invalid or unsupported executable format"

---

### Post by lordrick112 on 2009-02-12
Hey there!

Yeah, this happened to me during a reformat of my windows partition. Losing grub. This link helped me reinstall grub using a live ubuntu cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Hope this helps you out!

---

### Post by caljohnsmith on 2009-02-12
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by momitty on 2009-02-12
I uploaded the RESULTS.txt file.  I also uploaded the current menu.lst and then menu.lst.backup (it's missing the "11" kernel that it updated with a couple days ago)

Lordrick, I saw that post and tried that.  I don't know the exact error message, but essentially on the "root" step it said it wasn't a valid command.

---

### Post by caljohnsmith on 2009-02-12
OK, how about from the Live CD doing:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
sudo mount /dev/sda5 /mnt
sudo cp /mnt/boot/grub/menu.lst.backup /mnt/boot/grub/menu.lst
```
Then reboot, and let me know how far you get. We can work from there.

---

### Post by momitty on 2009-02-13
I'm back in business!

I actually copied from menu.lst~ instead of menu.lst.backup because the ~ version had the newest kernel listed in it.  

I opened up StartUp-Manager and changed the kernels to keep to 1 instead of 0.  I know I'm an idiot for setting it like that, and you probably aren't running Linux if you need somebody to always hold your hand...but shouldn't there be a warning on that thing? :)

Thank you both so much for your help.  It's great how a lot of people in the Linux community jump in and help somebody out!

---

### Post by wkhasintha on 2009-02-13
hi :D

---

### Post by caljohnsmith on 2009-02-13
That's great news you can boot again. Just one small suggestion, since you aren't using all those old kernels anyway, you can go into Synaptic Package Manager and uninstall the kernels you don't want so you can have that disk space back. I would recommend keeping one back up kernel that you know works in case you have problems with the most recent kernel. To uninstall the kernels in Synaptic, if you uninstall a "linux-restricted-modules-2.6.X-X-generic" package, it will also uninstall the "linux-image-2.6.X-X-generic" package that goes with it. Then you won't have to worry about those kernels being added to your menu.lst, and you will get the disk space back. Anyway, cheers and enjoy your Ubuntu install. :)

---

### Post by momitty on 2009-02-13
I didn't know you could uninstall them from there.  Thanks for the tip!

---

### Post by [.::MDT::.] on 2010-04-07
I installed Windows 7. Then Ubuntu 9.10.
Then, working in windows 7, next time I rebooted Grub disappeared!!! oO
I am trying to fix the grub now without any result. In attachment you can find my RESULT.txt file.

I tried:
```

grub> root (hd0,6)
root (hd0,6)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

Could you help me?
Thanks a lot, bye.

---

