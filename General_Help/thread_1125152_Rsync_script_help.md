---
title: "Rsync script help"
date: 2009-04-14
forum: General Help
---

### Post by bruno9779 on 2009-04-14
I need to write a little script to import and export all pics from an external HDD

My wife will do the same weekly so it isn't just a backup.

I have looked wide and far on the forums, and i came up with this:

```
#!/bin/sh

#push files
rsync -vurt --progress /home/bruno/Photos /media/Lacie/
#pull files
rsync -vurt --progress /media/Lacie/Photos /home/bruno/
```

It works very well for the push part, but when it gets to pull, it overwrites many (not all) pictures on my PC with the exact same copy on the ext HDD.

I guess it does this because the pics on the ext HDD have a newer modified date, but i am not sure

Please help

---

### Post by kpkeerthi on 2009-04-14
Is your external HDD FAT32?

---

### Post by bruno9779 on 2009-04-14
Yes Fat32.
My home is MS-free, so no need for NTFS.

I think the problem lies with the -u part of the script:
-u =  	skip files that are newer on the receiver

so, eg. when file A.jpg gets transferred to the ext HDD it gets a newer date. when HDD syncs with PC it finds that A.jpg is older on PC and replaces it.

I thought that -t would be a good workaround (-t = preserve times)
but not.

(on another instance, maybe something else causes this)

I would welcome very warmly a solution in a single command (if thre is any) but my actual knowledge doesn't get to that...

---

### Post by kpkeerthi on 2009-04-14
To sync b/w ext3 and fat32 (vfat) using rsync, you'll have to set the parameter "--modify-window=1" to gain a tolerance of one second to compensate for the differnces in time resolution in vfat compared to ext3.

This should sort it out:
```

sudo rsync -rout --verbose --progress --modify-window=1 /from /to

```

Change /from /to paths to match yours.

For more details, see [http://www.osnews.com/story/9681/The_vfat_file_system_and_Linux/page1/](http://www.osnews.com/story/9681/The_vfat_file_system_and_Linux/page1/)

---

### Post by megamania on 2009-04-14
> **bruno9779 said:**
> Yes Fat32.
My home is MS-free, so no need for NTFS.

If you only use Linux, why don't you format your external hd in a linux-friendly format? Ext3, for example.

Regarding your question, I'm not sure I understand exactly what you're trying to do with your push/pull scripts.
Are you attempting to send to the backup unit what's new, and then sync it to another computer? Apparently, you have two computers and a shared backup unit. How do you want to handle file deletions? For example, if you delete a picture from your computer, does it have to stay on the backup or not?

---

### Post by bruno9779 on 2009-04-15
I am not comfortable at all using fdisk, i had a look at it but i cannot make sense of the amount of commands it has, so I would need some extra help here.
(I had a bad experience with fdisk in the past, I chose some wrong setting on one of this Lacie drives and I killed it «god bless fnac no-fuss return policy») 

As you said it is a shared backup unit. I want to backup weekly the new pictures i add, and import whichever pic had backed up my wife on the same drive (I'm gonna set up a similar script on her laptop too).

No pictures get deleted or modified (i save them in a Gimp dedicated folder), so if they DO get deleted it is an error and they have to be re-imported.

Thanks

---

### Post by megamania on 2009-04-15
> **bruno9779 said:**
> I am not comfortable at all using fdisk, i had a look at it but i cannot make sense of the amount of commands it hasUse gparted. It's very easy: select the physical device, create/modify the partitions, format.

Obviously, be sure your data is backed up first!

---

### Post by tobydeemer on 2009-04-15
Hi-

I would agree w/ Megamania. If no Windows at home, just use Ext3 or other Linux filesystem at home. Chances are much better that you'll have longer "data integrity life" over Fat32.

have you tried options:

rsync -avzr --progress /source /destination

-a is archive mode, which implies keeping time stamps, permissions, other file attrs.

This also will not delete anything unless you use the --delete flag.

Hope that helps a bit...

---

