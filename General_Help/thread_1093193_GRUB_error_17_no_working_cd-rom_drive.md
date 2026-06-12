---
title: "GRUB error 17 no working cd-rom drive"
date: 2009-03-11
forum: General Help
---

### Post by ubuntumaybe on 2009-03-11
Hi,

I recently removed a partition and then increased the ubuntu partition size. When I boot I get the grub error 17. I do not have a working cd-rom drive so I cannot load the live cd. How can I get past the error 17 message and get the grub prompt? Thanks.

---

### Post by meierfra. on 2009-03-13
Try the Supergrub on  a floppy or USB-flash drive:

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by ubuntumaybe on 2009-03-13
Hi,

I cannot boot from a usb pendrive. I loaded puppy with its own grub but I cannot get access to it when the pc boots. I need to know if there is a way of bypassing the error 17 message and getting to the grub or linux prompt. I am working on removing the hd and putting it in another pc. Thanks.

---

### Post by meierfra. on 2009-03-13
> I need to know if there is a way of bypassing the error 17 message and getting to the grub or linux prompt.

No.  You need to be able to boot from some other device.

> I am working on removing the hd and putting it in another pc. 

That should work. Do you need instruction for reinstalling grub?

---

### Post by ubuntumaybe on 2009-03-14
Hi,

I managed to swap my problem hd with one on an old laptop. I am still having the problem. I have been checking the forum and I have tried some solutions. When I boot using a live cd I can see the data in all my partitions when I mount them. I have tried to update the mbr using the MEPIS cd which comes with a system option to update the mbr but still no solution. Now I get the grub prompt. When I try the root (hd0,0) option it tells me that it is an unrecognized command. Any help would be appreciated. Thanks.

---

### Post by meierfra. on 2009-03-14
In order to get a better picture of the current situation, boot from the Mepis LiveCD and download the Boot Info Script to  the desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and type:


```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by ubuntumaybe on 2009-03-16
Hi,

I took the hd and put it into an old laptop I still have. After many trials I managed to fix the problem. THanks.

joe

---

### Post by meierfra. on 2009-03-16
> After many trials I managed to fix the problem. 
Great. Have fun with Ubuntu.

---

