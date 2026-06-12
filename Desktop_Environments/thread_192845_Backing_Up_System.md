---
title: "Backing Up System?"
date: 2006-06-09
forum: Desktop Environments
---

### Post by SiKirk on 2006-06-09
Hi all,
I've just moved over to Linux, tried out FC5 and now settled with Ubuntu. 
Having just got my system all setup the way I want it, can someone tell me the easiest way of backingup my pc to DVD-RW's? I mean, I can use gnomebaker/nautilus to create data dvd's no problem etc etc, but something that will span disks is needed at some point.
I only have a single PC.. most things I've looked at seem aimed at distributed backups etc etc.

Thanks for any help you can give a new soul.:D 

-Si

---

### Post by frodon on 2006-06-09
Partimage is a popular linux tool to do that : [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by SiKirk on 2006-06-09
Thanks! That sounds something like what I'm after, I'll take a look.

-Si

---

### Post by frodon on 2006-06-09
However to restore a partition you may need a live CD (in the case you cannot boot on your linux partition) and unfortunatly the ubuntu live CD don't include partimage so you would need a live CD which contain partimage to restore the partition with a live CD like KNOPPIX for example.

---

### Post by SiKirk on 2006-06-09
Ahh.. there's always a catch isnt there. :)
Ok.. I'll try and get our systems admin to grab a knoppix .iso just incase.

-Si

---

### Post by arizonagroovejet on 2006-06-09
Can I ask, why DVD-RWs?

I would have thought an external harddisk would be a much simpler solution. You just plug it in and copy your files over. If you have Firewire in your PC get a harddisk with a Firewire connection - it's significantly faster than USB2 for this sort of thing. You can get an external drive quite cheap if you by the drive and the enclosure separately   and spend a few minutes with a screwdriver to put the former inside the latter.

After the first back up you can use rsync (you have that already) so only changes since the last back up are copied which, depending on how much has changed, will make the subsequent backups much quicker than the first one.

---

### Post by Getwild2 on 2006-06-09
[QUOTE=arizonagroovejet]Can I ask, why DVD-RWs?

I would have thought an external harddisk would be a much simpler solution. You just plug it in and copy your files over. If you have Firewire in your PC get a harddisk with a Firewire connection - it's significantly faster than USB2 for this sort of thing. You can get an external drive quite cheap if you by the drive and the enclosure separately   and spend a few minutes with a screwdriver to put the former inside the latter.

After the first back up you can use rsync (you have that already) so only changes since the last back up are copied which, depending on how much has changed, will make the subsequent backups much quicker than the first one.[/QUOTE]
Can I interrupt with a noob question?  In backing up your system, what would you choose to backup?  Obviously personal files but aside from that, system-wise what would you backup?  

I have an external firewire drive and would like to save myself a lot of trouble if worse came to worse during my time of noobness.  You should know that I have a /boot partition, /swap partition, /root partition and a separate /home partition.  

Thanks for your help and sorry to butt-in.

---

### Post by cotcot on 2006-06-09
Partimage allows you to backup and restore complete partitions. Save your MBR and partition table too. Partimage is a linux comparable to Ghost.

---

### Post by SiKirk on 2006-06-09
[QUOTE=arizonagroovejet]Can I ask, why DVD-RWs?

I would have thought an external harddisk would be a much simpler solution. You just plug it in and copy your files over. If you have Firewire in your PC get a harddisk with a Firewire connection - it's significantly faster than USB2 for this sort of thing. You can get an external drive quite cheap if you by the drive and the enclosure separately   and spend a few minutes with a screwdriver to put the former inside the latter.

After the first back up you can use rsync (you have that already) so only changes since the last back up are copied which, depending on how much has changed, will make the subsequent backups much quicker than the first one.[/QUOTE]


The largest storage device at the moment is my DVDR. I'll look into an external drive at some point, but all my cash is waiting for my holiday currently. 

-Si

---

### Post by lawngn0mex on 2006-06-09
[QUOTE=Getwild2]Can I interrupt with a noob question?  In backing up your system, what would you choose to backup?  Obviously personal files but aside from that, system-wise what would you backup?  

I have an external firewire drive and would like to save myself a lot of trouble if worse came to worse during my time of noobness.  You should know that I have a /boot partition, /swap partition, /root partition and a separate /home partition.  

Thanks for your help and sorry to butt-in.[/QUOTE]

You could setup a cron job to run to use dd.. throw  /boot and /home over.. then copy over /etc. 

All of the other directories are arbitrary, unless you've compiled some software and don't want to go through that again.

---

### Post by chalex on 2006-06-09
[QUOTE=Getwild2]Can I interrupt with a noob question?  In backing up your system, what would you choose to backup?  Obviously personal files but aside from that, system-wise what would you backup?  
[/QUOTE]

You probably just want to use [sbackup]("http://sbackup.sourceforge.net/HomePage"), which will walk you through the process.

---

### Post by aysiu on 2006-06-09
[QUOTE=frodon]However to restore a partition you may need a live CD (in the case you cannot boot on your linux partition) and unfortunatly the ubuntu live CD don't include partimage so you would need a live CD which contain partimage to restore the partition with a live CD like KNOPPIX for example.[/QUOTE] If you have enough RAM (I think 256 MB or above), you can always install PartImage with the Ubuntu live CD.

Details here:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

