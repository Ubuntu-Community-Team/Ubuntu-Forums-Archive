---
title: "Things are just missing"
date: 2009-03-12
forum: General Help
---

### Post by ozanamn on 2009-03-12
Hey all,

Just wondering if someone could give me a hand. When i was using my laptop yesterday my firefox hung due to trying to watch a .wmv file and when i loaded firefox again all my book marks are missing and my google search bar doesnt work. 

Also on the top tool bar under places my video picture and and music folders are all gone. 

I had just ran updates an hour before and i also had this problem before and i was going to to just update to 8.10 but i came back all of a sudden so didnt question it. im running 8.04 

Any help or if anyone has had this problem can they give me any insight into helping me out it would be great

Regards,
Oz :)

---

### Post by ozanamn on 2009-03-12
Also at the bottom of all windows it says that there is 0 bytes left on my hard drive when i know i had about 4gb and deleted a dvd off it there so should have freed up more and nothing. 

Thanks again,

Oz :)

---

### Post by theozzlives on 2009-03-12
Your Places stuff can be easily restored by dragging the folder to the lower leftt pane in Nautilus. FireFox keeps backups of your bookmarks. Go to Organize Bookmarks and import one of your backups. The addon  "FoxMarks" can help keep them current  should that happen again.  If you keep seperate partitions, you could be out of space in one and not the others. That would require  you resizing your partitions.

---

### Post by mb_webguy on 2009-03-12
It definitely sounds like your problems are due to a lack of space.  I had this problem a while back when I accidentally downloaded a large file to my small home partition rather than to my large data partition.

Did you delete that DVD to the trash, or permanently?  Items in the trash still take up disk space.

Try running the Disk Usage Analyser to see if your partition is really full, and if so what files and directories are taking up the space.

---

### Post by ozanamn on 2009-03-12
Its not even about restoring them. Like Gnome Do doesn't work anymore. Amsn wont run. i checked my hard drive on gparted and i have 2gb free on my hard drive. i don't have partitions. Just the one given to the whole system. Its really weird and hard to explain. like my flash videos don't work anymore in Firefox the search option doesn't work anymore.

Also just tried to restore my bookmarks from backup and nothing. 

Regards,
Scott

---

### Post by mb_webguy on 2009-03-12
Have you tried running the Disk Usage Analyser?  GParted isn't necessarily the best tool for reporting disk usage.

Could you post the output of the command "df -h" in the terminal?

---

### Post by ozanamn on 2009-03-12
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G   70G     0 100% /
varrun               1014M  248K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   40K 1014M   1% /dev
devshm               1014M   12K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-24-generic/volatile
overflow              1.0M   44K  980K   5% /tmp
gvfs-fuse-daemon       72G   70G     0 100% /home/scott/.gvfs
  


:) thank you

---

### Post by ozanamn on 2009-03-12
This happened before ages ago and i all of sudden turned it on a day or two later and it was working. Very strange.I ran the Disk Usage Analyser and everything looks normal. most of the space is dvd but im in the middle of burning them to disks.

---

### Post by mb_webguy on 2009-03-12
Based on this...```

Filesystem  Size  Used  Avail  Use%  Mounted on
/dev/sda1    72G   70G      0  100%  /
```
...you're definitely out of space, which is absolutely what's causing the problems.  Use the Disk Usage Analyzer to figure out where your space is being used, and either delete some things or move them to some kind of external storage.  And check your trash.  If you haven't emptied it in a while, this could be a big part of the problem.

You really shouldn't let your disk get this full.  Besides causing problems like you're having, letting your drive get this full will also absolutely result in fragmentation, even though Linux filesystems generally do a good job preventing it.  Running "sudo fsck -n" will tell you how badly your drive is fragmented.  (Make sure you use the "-n" option, by the way, since otherwise running fsck on a mounted filesystem could be a Very Bad Thing.)  You can defragment the files on the drive (but not the drive itself) using the python script in [this thread]("http://ubuntuforums.org/showpost.php?p=978381&postcount=1").

---

### Post by ozanamn on 2009-03-12
Well what do you know you where bang on. Deleted a few things and in seconds it all kicked back in. Wish there was someway to pay you back for your help. 
 

Thank you Thank you :):):)

Oz

---

