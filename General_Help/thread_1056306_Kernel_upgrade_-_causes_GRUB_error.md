---
title: "Kernel upgrade - causes GRUB error"
date: 2009-01-31
forum: General Help
---

### Post by tattrat on 2009-01-31
About two days ago I opted to install all the updates, including the kernel upgrade. Now the system will not boot: ```
root 75200e07-98bf-4c69-84d2-53c98d80740c
Error 11: Unrecognised device string 
press any key to continue
```
It was only after rebooting that I remembered that this also happened on the previous kernel upgrade. Last time I resolved the problem by booting the live CD and then editing the menu.lst (and possibly also fstab) to remove all UUIDs, to make the system bootable again. 
The problem this time round is that in the meantime this (rather old and crappy but nonetheless functional ) laptop has lost the ability to boot from cd.
my only option is booting from floppy. I have already attempted to fix the problem with supergrub floppy but i am not quite sure if, or how, to do it. 
Any help or alternative solutions would be appreciated!:D

---

### Post by cdtech on 2009-01-31
Just boot into the normal GRUB screen and press "e" to edit the kernel image line and replace it with the device name rather than the UUID. After you get into Linux then edit your GRUB menu list........

---

### Post by tattrat on 2009-01-31
Thanks for the quick response. 
I have altered the first line from ```
root 75208e07-98bf-4c69-84d2-5398d80740c
``` to 
```
root   (hd0,0)
```
And the second line from 
```
kernel  /boot/vmlinuz-2.6.27-11-generic root=UUID=750208e07-98bf-4c69-84d2-5398d80740c ro quiet splash
```
to
```
kernel /boot/vmlinuz-2.6.27-11-generic root (hd0,0) ro quiet splash
```
Doing this starts fine but the splash progress car never notes and I get chucked into busybox. The last error is 
```
Loading, please wait... 
gave up waiting for root device.  common problems: 
 - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
     - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! does not exist. Dropping to a shell! 
```
As far as I can remember the disk has one ext2 partition and a swap. Have I got the syntax wrong? If not, what shall I do next? 
what a challenge typing all that on a phone!

---

### Post by caljohnsmith on 2009-01-31
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop (Live CD is fine), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by tattrat on 2009-01-31
Unfortunately this machine on longer has the ability to boot from cd. Booting from floppy is currently my only option. Previously, when this machine was able to boot from cd I was able to fix this!

---

### Post by Yashiro on 2009-01-31
> kernel          /boot/vmlinuz-2.6.27-11-generic root=**/dev/sda1**  ro quiet splash
As above.Your problem is you've transferred the system at some point and the auto grub is using your old kopt string.

Look for # kopt=root=UUID=75208e07-98bf-4c69-84d2-5398d80740c in menu.lst and replace that uuid with the uuid of the partition you boot from.

or

> root 75208e07-98bf-4c69-84d2-5398d80740c
should be root**=**75208e07-98bf-4c69-84d2-5398d80740c

---

### Post by tattrat on 2009-01-31
```
kernel /boot/vmlinuz-2.6.27-11-generic root=/dev/sda1 ro quiet splash 
```
has allowed me to boot.

As for the change the line with UUID, i have never made any changes to menu.lst or added any partitions. The previous kernel upgrade caused the same problem, just that time round i coukd fix it by using the kive cd.

I am sure the uograde process should not mess this up. Still i have learned how to alter the menu.lst on the fly, and will know how deal with it in future!

Thanks all round.

---

### Post by Yashiro on 2009-01-31
if you modify the #kopt= line as I said your system will survive upgrades in the future. At least, it should. :D

Or just make it #kopt=root=/dev/sda1 ro

---

### Post by NotoriousMOK on 2009-02-02
smoking the UUID reference here fixed me too -- thank you!

---

### Post by tattrat on 2009-02-03
It turns out that the #kopt and #groot were correct and set up with UUIDs.

The problem with my system is, that since I increasee the size of the swap partition and reduce the size of the root partition, it just won't boot using UUIDs in menu.lst, even though they are correct ones. It seems fine with UUIDs in fstab.

---

### Post by Yashiro on 2009-02-03
You might need to update your init (update-initramfs). 
You can also stop ubuntu running update-grub on kernel updates too. (/etc/kernel-img.conf)

---

### Post by tattrat on 2009-02-03
> **Yashiro said:**
> You might need to update your init (update-initramfs)


Is this a console command?

---

### Post by Yashiro on 2009-02-03
*update-initramfs -u *I believe, look it up before you do it.

---

