---
title: "Grub Error 21"
date: 2008-12-28
forum: General Help
---

### Post by Hyter on 2008-12-28
I have to IDE hard drives plugged into my computer. The master has Ubuntu on it and the slave has Windows XP. When I select Windows XP in grub it gives me an error 21. I think the menu.lst is wrong.

Here is my menu.lst:

```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		b2c67708-a32e-499a-8c7e-dad4c3fe1d92
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b2c67708-a32e-499a-8c7e-dad4c3fe1d92 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

<Removed recovery mode, and memtest>

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by mayonaise15 on 2008-12-28
I did some searching on Google and found out that grub error 21 means "Disk not found."  I would double check that you can see both disks in the BIOS as well as checking the jumper settings on both drives.  Hope that points you in the right direction.

---

### Post by pietjanjaap on 2008-12-28
First make copy of the file.

This is just a gues:
Change this:


root		(hd0,1)   


Or

map		(hd1) (hd0)
map		(hd0) (hd1)

---

### Post by caljohnsmith on 2008-12-28
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

