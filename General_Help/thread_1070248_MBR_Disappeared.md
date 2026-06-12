---
title: "MBR Disappeared"
date: 2009-02-14
forum: General Help
---

### Post by vandorjw on 2009-02-14
Hi,

I have a computer with 2 hard drives.
Windows XP was installed on the 500GB First. Partitioned into 60GB winXP and 400 DATA-Storage.

I then installed vista to the other Hard Drive from inside win XP. 
(Vista would not boot from CD for some odd reason)

So, for a while, vista and XP lived happily together.

Today, I decided to remove windows XP and install Ubuntu 8.10 in its place.
Being, not smart, I disconnected the hard drive containing Vista so that nothing would happened to it if my ubuntu install failed.

When I finished installing Ubuntu, I re-attached vista drive. 
I edited grub by adding the following.

> 
title		Other operating systems:
root

title		Windows Vista
root		(hd1,0)
makeactive
chainloader	+1


when I tried to boot vista, it first told me no MBR found, press ALT-CTR-DEL to reboot.

I didn't have a Vista CD with me at the time so I used ubuntu to give vista an MBR.

```

1) download ms-sys
2) compile and install
3) sudo ms-sys -m /dev/sda1
   --> results in succesfully written win2k, xp 2003 mbr to sda1

```

So I reboot, and now it hangs at 
> 
123FA


Does anyone know what I should do. (I don't want to re-install windows and restore grub) - Restoring Grub is easy..Vista's MBR is horrible to work with.

I am going to find out what happens when I boot from a Vista CD.
I don't know if it has a restore or startup-repair option.

If anyone has any ideas on how to fix Vista's MRB let me know.

Cheers - CC7

---

### Post by dcstar on 2009-02-15
> **cc7gir said:**
> Hi,

I have a computer with 2 hard drives.
Windows XP was installed on the 500GB First. Partitioned into 60GB winXP and 400 DATA-Storage.
........
I am going to find out what happens when I boot from a Vista CD.
I don't know if it has a restore or startup-repair option.

If anyone has any ideas on how to fix Vista's MRB let me know.

Cheers - CC7

Assuming these are SATA drives, swap the cables on the MB and see if Windows now boots.

If it does, then leave them as they are and re-install Ubuntu onto the second drive.

---

### Post by caljohnsmith on 2009-02-15
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. The results of that script will help clarify your setup and hopefully what the solution to your Vista booting problem might be.

---

### Post by vandorjw on 2009-02-15
delete post please (irrelevant info)

---

### Post by vandorjw on 2009-02-15
I cannot run the script anymore (unless from a live disk) because I can no longer boot into ubuntu.

I just went with the path of least resistance and reinstalled vista.
I managed to move all data to the Data partition.

1 Drive is a 500 GB SATA Drive.
1 Drive is a 250 GB IDE Drive.

250 GB = Vista

500 GB = 
- 400 GB Data Partition;
- 60 GB ubuntu;
- 2 GB swap
- 200 mb /boot

I would like to install Grub to /boot.

Any Advice?

When Ubuntu started (before I re-installed Vista) I remember seeing that it booted from hd(1,6).

I will try to run that script from a live disk but I am not sure if that will help you.

Cheers - CC7

---

