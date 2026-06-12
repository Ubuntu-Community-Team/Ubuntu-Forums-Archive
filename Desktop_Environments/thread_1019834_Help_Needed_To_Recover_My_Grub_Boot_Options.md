---
title: "Help Needed To Recover My Grub Boot Options"
date: 2008-12-23
forum: Desktop Environments
---

### Post by nullfactor on 2008-12-23
Hi folks... long time no post.

Since last time, I have convinced my father to give Ubuntu a try.  He loves it, by the way.  However, he still wanted to hold on to a Windows partition, just for a security blanket.  How ironic that he wanted Windows to feel secure, hmm? heh heh

At any rate, and of no surprise, my father encountered a nasty little virus that more or less infected all of his Windows system files.  Thinking he was doing the right thing, he selected to have the infected files deleted (give the guy a break... he's in his 60s and not very good with machines).  

Today, I reformatted and re-installed Windows on his NTFS partition, leaving the Ubuntu partition untouched.  However, when I boot the system, it automatically goes into Windows.  Grub does not appear, giving the choice to boot into Ubuntu.

Any ideas as to how to get Grub to appear, again, without having to reinstall the Ubuntu partition, as well?

Additional info:  the version of Windows in questions is XP Home 32-bit.

Mucho thanks, in advance.

+dharvell

---

### Post by kellemes on 2008-12-23
Download/Burn [Super Grub Disk]("http://www.supergrubdisk.org/") and have it fix Grub based on /boot/grub/menu.lst in your Ubuntu /boot-partition.

---

### Post by ajgreeny on 2008-12-23
You already have the ubuntu live CD so can use that to restore grub.

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by nullfactor on 2008-12-23
Thanks...

But your last sentence worries me.  *HOPEFULLY* I will have a working GRUB bootloader.  And if something goes wrong?  How screwed would I be?

Thanks.

> **ajgreeny said:**
> You already have the ubuntu live CD so can use that to restore grub.

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by nullfactor on 2008-12-23
AJGREENY - Are you sure of your directions?

I got to where it says:  setup (hd0)

I get:

Error 12:  Invalid device requested

Please double check your directions and let me know what you find.

Thanks.

---

### Post by nullfactor on 2008-12-23
Nevermind... 

I just went with kellemes' advice and it worked really, really well.

Thanks, kellemes!

+dharvell

---

### Post by ajgreeny on 2008-12-23
hd0, that is zero, not cap O.  You must have an hd0, surely?  Lets see the output of ```
sudo fdisk -l
``` from the terminal in live CD.

As for the HOPEFULLY, all I can add is that this method has not let me down ever, though it does depend on the /boot/grub/menu.lst file being correct.  If it should go wrong you can always restore the windows MBR to get back to where you are at the moment, but you will be no worse off even if it is unsuccessful.

---

