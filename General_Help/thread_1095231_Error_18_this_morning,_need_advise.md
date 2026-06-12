---
title: "Error 18 this morning, need advise"
date: 2009-03-13
forum: General Help
---

### Post by lindsay7 on 2009-03-13
I have a dual boot vista/Ubuntu 8.10 that has been booting and running just fine. Over night windows must have installed an update and restarted or something caused a restart. When I went to my computer, there was an Error 18; Seledted cylinder exceeds max. supported by bios screeen showing. I turned the computer off and it restarted in windows. I have not tried to boot into Ubuntu yet as my wife is needing to get her work done in quicken before I can get to it.

This is a single hard drive installation with a 250gig drive that is partitioned 50/50% between windows and vista.

Can somebody give me any ideas on what is going on with this.

---

### Post by meierfra. on 2009-03-13
> something caused a restart.

Maybe you had a power outage. 
Anyway, I suggest  a file system check and reinstalling grub:

Boot from the Ubuntu LiveCD, open a terminal and type

```

sudo umount /dev/sda5
sudo e2fsck -fyv /dev/sda5
``` 
(here  /dev/sda5 has to be replaced by the device name of your Ubuntu partition. Use "sudo fdisk -lu" to determine the device name)

```
sudo grub
```

and at the grub prompt:


```
 find /boot/grub/stage2 
```

This will return (hd0,X), where X is some number,  like (hd0,4)

Still at the "grub>" prompt:


```
root (hd0,X)
setup (hd0)
quit

```

(here X  needs to be replaced by the number you got from "/find /boot/grub/stage2")


You might also check your bios and see whether some of the setting of have been  messed up.


**If this did not solve your problem  or  you need  more help**

Boot from the Ubuntu Live CD and download the Boot Info Script to desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by lindsay7 on 2009-03-14
Here is the info from my drive. It booted into Ubuntu and seems to be working OK now. Please take a look at this info and let me know if you see anything that is out of line

```
rub> find /boot/grub/stage2 

(hd0,4) 



grub> 





Disk /dev/sda: 250.0 GB, 250059350016 bytes 

255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors 

Units = sectors of 1 * 512 = 512 bytes 

Disk identifier: 0x4bc36f5f 



Device Boot Start End Blocks Id System 

/dev/sda1 * 2048 341204534 170601243+ 7 HPFS/NTFS 

/dev/sda2 341204535 488392064 73593765 5 Extended 

/dev/sda5 341204598 482303429 70549416 83 Linux 

/dev/sda6 482303493 488392064 3044286 82 Linux swap / Solaris 



Disk /dev/sdb: 1019 MB, 1019215872 bytes 

255 heads, 63 sectors/track, 123 cylinders, total 1990656 sectors 

Units = sectors of 1 * 512 = 512 bytes 

Disk identifier: 0x0accb65c 



Device Boot Start End Blocks Id System
```

---

### Post by meierfra. on 2009-03-14
> It booted into Ubuntu and seems to be working OK now

Good news. Just curious: did "e2fsck" fix any errors? Did you have to adjust some settings in the  "bios"?


> Please take a look at this info and let me know if you see anything that is out of line

Looks normal.

---

### Post by lindsay7 on 2009-03-14
I did not have to do anything. The system booted to Ubuntu when I restarted from windows. I did go into the bios and noticed that the floppy drive (which I do not have) was showing as active, I disabled it. Other that that nothing in the bios was out of line. I guess I have to see if this grub error shows up again (hope not).

Thanks again for taking the time to look at this for me. I have put Ubuntu on four computers this month and this is the first time that I have seen the evil grub error show up. I could not be happier with Ubuntu on my systems and the forums have been a super great help in making this transaction enjoyable.

Thanks to all!

---

### Post by meierfra. on 2009-03-14
> I did not have to do anything. 
That's an easy fix. :)

> I guess I have to see if this grub error shows up again (hope not).

I have seen Grub Error 18 occur in random situations. So I would  guess that there is nothing wrong with Grub or Ubuntu, and   the Grub error was just caused by the strange reboot.

---

