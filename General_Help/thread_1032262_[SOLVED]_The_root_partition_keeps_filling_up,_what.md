---
title: "[SOLVED] The root partition keeps filling up, what to do?"
date: 2009-01-06
forum: General Help
---

### Post by mamboze on 2009-01-06
The / (root) directory of my computer, Ubuntu Hardy, had filled up completely for the second time in a month. This happened after I mounted an external hard disk for system backup and other storage, but I'm not sure that's the cause. I've also moved all my music files (around 100Gb) to the external drive. The first time it happened I increased the size of /dev/sda1 (root) partition, but it has filled again. 

I've checked ths sizes of the folders in / and two are very large, /var  27.8 Gib, /media 43.8 Gib. The folders in /media look a bit weird, like
cdrom, cdrom0, cdrom2, disk, disk-1, disk-2, disk-3, disk-4. disk-5, Kingston, Kingston_, Kingston__, Kingston___ and so on.

In the last few days, my two printers have been sporadically not detected and Firefox has not been accessing the net. I've checked the router and the hub, these are OK. 

The 320 Gb HD is partitioned like this:

Partition    Filesystem    Mountpoint    Size          Used  
/dev/sda1     ext3          /           47.19 Gib     47.19 Gib
/dev/sda2        linux swap	         3.77 Gib	-
/dev/sda3     ext3          /boot       478.5 Mib     79.46 Mib
/dev/sda4   extended 
/dev/sda8     ext3          /home       97.65 Gib      9.92 Gib
/dev/sda7     ext3          /tmp         9.32 Gib    224.57 Mib
/dev/sda6     ext3          /var        64.75 Gib     28.38 Gib
/dev/sda5     ext3          /opt         9.77 Gib    361.31 Mib         

If necessary, i would be happy to do a clean install of 8.10. I read somewhere that it is possible to do this without losing data, with a precautionary backup. Could anybody confirm this and tell me how it is done.  

Any help would be most welcome. TIA

---

### Post by drs305 on 2009-01-06
A likely cause is there are large log files being generated in the /var/log directory. You can do searches by file size for particularly large files or investigate the directories to find out if there are numerous smaller files taking up space.

You can see the space taken up by each /var folder with:
```

sudo du -h /var  # or narrow the search to /var/log

```

The large size of the /media folder may be due to the fact that your other drives are mounted in /media and are thus included in the totals. The folders you mentioned are the devices which are mounted in the /media folder.

To investigate what is taking up so much space, take a look at this link. It primarily discusses hidden trash but also covers how to find other files filling up your drive:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by mamboze on 2009-01-06
Thanks drs305
I've deleted the trash directories and a backup directory /var/backup with a large tgz file (around 30Gb, I think)

But  running df -Th | sort gives

/dev/sda1     ext3     47G   47G     0 100% /
/dev/sda3     ext3    464M   65M  376M  15% /boot
/dev/sda5     ext3    9.7G  282M  9.0G   3% /opt
/dev/sda6     ext3     65G  540M   61G   1% /var
/dev/sda7     ext3    9.3G  150M  8.7G   2% /tmp
/dev/sda8     ext3     97G  9.2G   83G  10% /home

there's no change in / , but, with gksudo nautilus, /var properties shows contents 2.3Gb and free space 60.5GB, /usr properties shows free space 0Gb. This seems strange to me. why the variation. Am I misunderstanding what 'free space' means here.

---

### Post by timcredible on 2009-01-06
a normal root partition has about 3-4GB used on it.  as long as user's home directories are located on another partition (make sure users are in /home, not /) then you shouldn't need more than 4GB for /.

as for /media, that's where the external disk gets mounted.

as for running out of space - if you did run out of space at some point, it's hard telling what got messed up - a re-install may be a good solution if that happened.

---

### Post by drs305 on 2009-01-06
> **mamboze said:**
> Thanks drs305
I've deleted the trash directories and a backup directory /var/backup with a large tgz file (around 30Gb, I think)

there's no change in / , but, with gksudo nautilus, /var properties shows contents 2.3Gb and free space 60.5GB, /usr properties shows free space 0Gb. This seems strange to me. why the variation. Am I misunderstanding what 'free space' means here.

Did you delete the large .tgz file using "gksudo nautilus"? If so, did you use SHIFT-DELETE to delete the Trash folder? If you didn't, the file would have been deleted and moved to .... the trash folder. Using SHIFT-DEL ensures the trash is permanently removed.

As for the free space showing for /var and /usr, are the results from the Properties, free space and both done at relatively the same time? Assuming both folders are located in / , the total remaining displayed at the bottom of the Properties page should be the same since it is looking at free space available on the partition.

---

### Post by mamboze on 2009-01-10
Sorry for the delay in replying, I've been away from my machine for a couple of days. 

I'm not sure what caused the problem in the first place. It could have been due to the backup files being generated by sbackup , not sure about this just surmising. At any rate I did a clean install of 8.10.

Things are OK now, but obviously, there is a need for preventive maintenance. Just good practice, I guess. And I think I'll look around for another backup package. 

Thanks to both of you for your help.

---

