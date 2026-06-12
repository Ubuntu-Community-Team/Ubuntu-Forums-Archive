---
title: "Grub wont boot windows xp"
date: 2009-03-01
forum: General Help
---

### Post by markk1994 on 2009-03-01
Hey Ive tried booting to Windows and Grub gives me error 
Unexpected Device String please help me as I need to get on Windows to get something for my school ASAP.

This is my current Menu.lst I know I screwed up the Windows part . 

```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic
he rootnoreply statement. Here is the current Windoze section:
title		Ubuntu 8.10, memtest86+
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/memtest86+.bin
quiet

title		Windows 95/98/NT/2000
root		(hd1,4)
makeactive
chainloader	+1
```

---

### Post by markk1994 on 2009-03-01
Hey Ive tried booting to Windows and Grub gives me error
Unexpected Device String please help me as I need to get on Windows to get something for my school ASAP.

This is my current Menu.lst I know I screwed up the Windows part . 

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5855328f-2672-4e41-9e7b-752b01b38af9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic
he rootnoreply statement. Here is the current Windoze section:
title		Ubuntu 8.10, memtest86+
uuid		5855328f-2672-4e41-9e7b-752b01b38af9
kernel		/boot/memtest86+.bin
quiet

title		Windows 95/98/NT/2000
root		(hd1,4)
makeactive
chainloader	+1
```

---

### Post by Despell1 on 2009-03-01
its hda, not hd1

---

### Post by jyaan on 2009-03-01
You probably have the wrong partition listed. (hd 1,4) means that it is the second drive, fifth partition. So this would be /dev/sdb5. If you find out the correct device I can tell you what you need in there. Also you will need to use 'map' to trick Windows into thinking it is on the primary hard disk. It's very picky and won't let you run it from elsewhere.

---

### Post by louieb on 2009-03-01
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
    
     ```
sudo bash ~/Desktop/boot_info_script*.sh 
```That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Windows from Grub.

The script was written by a couple of regulars in the forum. It will give all the info needed to get you giong again.

---

### Post by bodhi.zazen on 2009-03-01
Threads merged, duplicate post deleted.

---

