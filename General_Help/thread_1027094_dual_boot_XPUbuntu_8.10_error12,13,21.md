---
title: "dual boot XP/Ubuntu 8.10 error12,13,21"
date: 2008-12-31
forum: General Help
---

### Post by ubuntoooooo on 2008-12-31
While most of you have probably left or are geared up for your new years I present you with this little error I've been having as of late. I reinstalled my Ubuntu partition mostly without choice, but regardless Windows XP was sitting fine alone for some time.

Now I've reinstalled Ubuntu 8,10, I'm on it now in fact. But when I try to boot back into windows XP (for gaming mostly, but also other various reasons) I get those 3 windows errors right off the bat. error 12, error 13, error 21. 
They come from various fixes I've tried as I've scoured the forums here.

A readout on my boot/grub/menu.lst:

```
## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-9-generic
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=3f0bf174-4a6e-4256-8794-34b2788f5a4a ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=3f0bf174-4a6e-4256-8794-34b2788f5a4a ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=3f0bf174-4a6e-4256-8794-34b2788f5a4a ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=3f0bf174-4a6e-4256-8794-34b2788f5a4a ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

####

title 		Microsoft Windows XP Professional
root	 	(hd0,1)[COLOR="Red"]<--When set as this I get stuck in "Starting Up..."[/COLOR]
chainloader 	+1
savedefault
makeactive
```

---

### Post by caljohnsmith on 2009-01-01
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by alzie on 2009-01-01
> title 		Microsoft Windows XP Professional
root	 	(hd0,1)[COLOR="Red"]<--When set as this I get stuck in "Starting Up..."[/COLOR]
chainloader 	+1
savedefault
makeactive

I think root should be (hd0,0)

To change this open a terminal and run

> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
        (this will make a backup of menu.lst)
sudo gedit /boot/grub/menu.lst
        (to make changes in menu.lst)

After you make your change, save and close gedit.

I hope this helps

---

