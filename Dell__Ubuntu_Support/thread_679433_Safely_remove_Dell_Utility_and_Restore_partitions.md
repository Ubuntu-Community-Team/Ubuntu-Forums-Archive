---
title: "Safely remove Dell Utility and Restore partitions"
date: 2008-01-27
forum: Dell  Ubuntu Support
---

### Post by Phrazzled on 2008-01-27
I am dual booting Windows XP and Ubuntu using GRUB, on a Dell E520 Dimension. I don't need the OEM installed Dell Utility and Dell Restore partitions because I have saved images of both OSs and all data files. 

To have more room on HD #1, and also to make available an extra primary ext3 partition, I would like to delete both Dell partitions.

My concern is that: simply deleting these partitions could upset GRUB bootloader and/or that changing partition numbers could confuse the Windows boot.ini file.
It's my understanding that the MBR and GRUB only use the first 15 sectors of the HD's first track which is 'outside' all normally visible partitions ; so these shouldn't be affected?

I'd appreciate it if you cared to share your experiences with this process. Please include description of any pitfalls to avoid.

Thank You

---

### Post by Phrazzled on 2008-01-27
I guess I might as well begin answering my own question, at least partly.

I figured that there was no harm in deleting the Dell Restore partition at the end of HD #1. Installing GRUB had already overwritten the Ctr + F11 restore function anyhow.

I deleted the Dell Restore partition using a live CD of Gparted; but was too scared to delete the Utility partition thinking it might interfere with system booting. I left it in place as it is only 39 MB and does no harm.

As soon as I can find suitable Linux replacements  for all my vital MS Windows apps I'll be ditching Win XP and never intend to buy MS products again, or PCs that come with OEM installed operating systems and their unwanted baggage.

If anyone has anything to add re deleting  Dell's Utility partition I welcome their comments.

---

### Post by Ice.Polar on 2008-01-27
Moin, moin,

I have installed ubuntu 7.04 on a Dell Optiplex with removing any existing partitions. On a testdrive i couldnt see any troubles...
I changed since a year to linux and ubuntu is ok.
  Ice

---

### Post by oneheaton on 2008-06-05
I'm in much the same situation as you.  After deleting the Dell utility partition i found that i could not boot my windows xp anymore.  The error says missing or corrupt hal.dll.  Apparently this is a problem with the boot.ini file (i think) not the hal.dll file, but i have not yet figured out exactly what to edit in the boot.ini file. 

If anyone has resolved this problem please post some help.

---

### Post by sayantandas on 2008-06-11
> **oneheaton said:**
> I'm in much the same situation as you.  After deleting the Dell utility partition i found that i could not boot my windows xp anymore.  The error says missing or corrupt hal.dll.  Apparently this is a problem with the boot.ini file (i think) not the hal.dll file, but i have not yet figured out exactly what to edit in the boot.ini file. 

If anyone has resolved this problem please post some help.

hi,
if u have ubuntu installed in ur computer, and still cannot boot into either xp or ubuntu then do this

1. boot up with ubuntu live cd/dvd
2. open terminal and type sudo grub
3. u will get a prompt like this   
   
    grub>

4. now type find /boot/grub/stage1
5. u will get an info in which partition ubuntu is installed. it will show something like this.
    
   (hdx,y),   where x is hard drive no. and y is the partition no.

6. then  type 

root (hdx,y)
setup hdx
quit


and then reboot.

if this doesnt work, access internet from cd and download and install auto super grub from the internet. and follow the onscreen instructions

hope this helps

---

