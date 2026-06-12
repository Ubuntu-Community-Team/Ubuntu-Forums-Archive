---
title: "space disappeared after cloning drive"
date: 2009-04-03
forum: General Help
---

### Post by callie510 on 2009-04-03
So I decided to wipe & repartition my drive so I could give my Ubuntu /home directory a little more space. I used Macrium Reflect.

I cloned a 52.6 GB drive into a 110 GB partition. Figured it would just copy the files. Oops. Now, strangely, all the extra space has disappeared.

-- My /home directory lists as the wrong size (52.6 GB)
-- fdisk -l lists the partitions right
-- Gnome Partition Editor sees a 110 GB partition, but all the extra space is filled. (with what?!)

Any ideas on how to recover 60 gb of lost space ....?

---

### Post by ibuclaw on 2009-04-03
Would you mind posting the output of
```
sudo fdisk -l
```
and a screenshot of GParted listing the filesystems so people can see what is happening and get an overall better picture of just what is going on?

Regards
Iain

---

### Post by callie510 on 2009-04-03
Sure:

[IMG]http://i43.tinypic.com/6gepo1.jpg[/IMG]

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04615fc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       19457   130688775    f  W95 Ext'd (LBA)
/dev/sda5            3188       18182   120447306   83  Linux
/dev/sda6           18183       19266     8707198+  83  Linux
/dev/sda7           19267       19457     1534176   82  Linux swap / Solaris

---

### Post by ibuclaw on 2009-04-03
hmm...

Do you use any software that creates large files, such as VirtualBox, for instance?

Try running **du** with a pattern filter so you can see just **what** directories are eating up the space and **where**

```
sudo du -h /home | sed '/[0-9]*\.[0-9]*G\s*/!d'
```

Regards
Iain

---

### Post by callie510 on 2009-04-03
I already tried running a command to list the biggest files, and didn't find anything unusual, but I like your command better! Thanks!

sudo du -h /home | sed '/[0-9]*\.[0-9]*G\s*/!d'

du: cannot access `/home/kmacnich/.gvfs': Permission denied
1.9G	/home/kmacnich/Music/iTunes Music/Paul van Dyk
1.2G	/home/kmacnich/Music/iTunes Music/DJ Doboy
2.9G	/home/kmacnich/Music/iTunes Music/Compilations
1.1G	/home/kmacnich/Music/iTunes Music/Unknown Artist
2.4G	/home/kmacnich/Downloads
4.8G	/home/kmacnich/.VirtualBox/VDI
4.8G	/home/kmacnich/.VirtualBox
3.8G	/home/kmacnich/Pictures/Windows Pictures
5.7G	/home/kmacnich/Pictures
1.5G	/home/kmacnich/NEW Music
2.6G	/home/kmacnich/Documents/Windows Documents
2.6G	/home/kmacnich/Documents
1.5G	/home/kmacnich/Desktop/psp/games
1.7G	/home/kmacnich/Desktop/psp
1.2G	/home/kmacnich/Desktop/CASIO digital camera/Image Library
1.2G	/home/kmacnich/Desktop/CASIO digital camera
4.7G	/home/kmacnich/Desktop

Nothing out of the ordinary... that all pretty much adds up to the 40ish GB that should be used. Not 110.

So strange. I might just copy all the files, wipe the partition, and put them back.

---

### Post by callie510 on 2009-04-03
ugh. I don't know why my root partition is all full too - it used to have a few gigs free. I thought 8 gb was enough....

If I'm going to backup all my files, wipe the drive, and put them back, can someone suggest a good way to do this? Isn't there a dd or rcopy command that will do it?

---

### Post by drs305 on 2009-04-03
> **callie510 said:**
> ugh. I don't know why my root partition is all full too - it used to have a few gigs free. I thought 8 gb was enough....

A few  things come to mind. The root trash bin has trash in it that hasn't been emptied, you have some large log files taking up space, or backup files ended up on the system partition instead of on another drive. 

To look at your root trash:
```
gksudo nautilus /root/.local/share/Trash/files
```
Use SHIFT-DEL to remove the files.

Find large files:
```
sudo find / -name '*' -size +500M
```
Few if any system files are larger than this.

My signature line has a link to a Trash guide that provides more things to investigate.

---

### Post by callie510 on 2009-04-03
The trash command you gave me doesn't work ... I don't have that directory? However, I will check out your sig :)

Anyone have any clues on my 60GB of mysteriously missing space?

---

### Post by drs305 on 2009-04-03
callie510, my apologies, I had a typo in "share". Please try the command again.

Did you go through the options in the Trash guide. It covers more than trash (and doesn't have any typos - at least that haven't been corrected  ;-)  ).

---

### Post by kpatz on 2009-04-03
> **callie510 said:**
> I cloned a 52.6 GB drive into a 110 GB partition. Figured it would just copy the files. Oops. Now, strangely, all the extra space has disappeared.If you cloned a filesystem image, you still have a 52.6 GB filesystem in your 110 GB partition.

Use the **resize2fs** command to expand your ext2/3 filesystems to utilize the space in the larger partition.

It's a good idea to unmount /home first (though it's not necessary).  Boot into a recovery console so you can log in as root, and dismount /home.  Then use the command **resize2fs -p /dev/sda5**.  When it's done, exit the recovery console, let it boot normally, and you should have the extra space in /home.

---

### Post by callie510 on 2009-04-03
> **kpatz said:**
> If you cloned a filesystem image, you still have a 52.6 GB filesystem in your 110 GB partition.

Use the **resize2fs** command to expand your ext2/3 filesystems to utilize the space in the larger partition.

It's a good idea to unmount /home first (though it's not necessary).  Boot into a recovery console so you can log in as root, and dismount /home.  Then use the command **resize2fs -p /dev/sda5**.  When it's done, exit the recovery console, let it boot normally, and you should have the extra space in /home.

YESSSS~!!! Thank you! I did this and it worked! All my free space came back. You are so right, I had a 52 GB filesystem on my 110 GB partition, and I had to resize the filesystem.

Thanks everyone for your help!

---

