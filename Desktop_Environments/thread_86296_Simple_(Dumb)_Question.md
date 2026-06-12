---
title: "Simple (Dumb) Question"
date: 2005-11-04
forum: Desktop Environments
---

### Post by tagg3rx on 2005-11-04
How can I see how much space i have left on my hard drive?

/me smacks self with a large trout

Thanks,
:KS Tagg3rX :KS

---

### Post by joscar on 2005-11-04
Syetem --> Administration --> Disks

---

### Post by Joe_lurker on 2005-11-04
If you are into the command line type:
```
df -h
```
-Joe

---

### Post by tagg3rx on 2005-11-04
intresting the df -h shows the freespace 
but for some reason the graphical disk manager says : size 9.29 GiB (Freespace not Avialable)

odd...

---

### Post by tagg3rx on 2005-11-04
ahh it says its unformatted
But wont let me format or enable it

---

### Post by Rule on 2005-11-04
you can use "cfdisk" in the terminal to format it.

---

### Post by tagg3rx on 2005-11-07
Ok this isnt as simple as it should be....  Or atleast my perception there of is getting a bit amplified being a monday and all....

So I do a sudo cfdisk
and get 2 Harddrives listed hda1 and hda5
I select 
hda5      (blank)    Logical   Linux LVM   (blank)     997.27
Select write as it seems the closest to format

It says Wroet Partition table, but re-read table failed reboot to update table

So I rebooted

Loaded up system - admin - disks 
Choose Hard disk > Partitions tab and have 2 partitions hda1 looks fine
hda5 indicates:
access path none (i have tried changing to home)
size 9.29 GiB (free space not avial)
Status Inaccessible

I have clicked format and a status bar jumps to 100% but nothing happens
I have clicked enable and it goes grey but comes back the same

So how do I format this drive (and make it the default place where I save data)

Thanks ubuntus
:KS Tagg3rX :KS

---

