---
title: "Beagle with vfat discs?"
date: 2006-02-20
forum: Desktop Environments
---

### Post by Belfagor on 2006-02-20
hi! how can i make beagle search my win discs? they are vfat formated.. thanks from now on!

---

### Post by RAOF on 2006-02-20
Just add the places you've mounted the windows partitions to the list of directories that beagle searches.  You should be able to do that through the "search preferences" item in System->Preferences.

---

### Post by Belfagor on 2006-02-20
alrady did... but no change still doesn t search my windiscs...

---

### Post by RAOF on 2006-02-20
It'll take some time to index them.  Also, do you have read permissions (ie: can you read from them / copy from them) to them?  There's no reason I know why beagle couldn't index vfat partitions.

---

### Post by Belfagor on 2006-02-20
yes i can.. and here is the fstab content..(just 1 row)

/dev/hda1               /mnt/win1              vfat umask=0,defaults,rw 0 0

---

### Post by RAOF on 2006-02-20
So you've added /mnt/win1 etc to the list of directories to search in beagle-settings...  Hmm.

You can check what beagle is doing with the command "beagle-info --status".  Check that out - see if it's indexing anything from your windows drives.  It will probably be slower to index them than your linux native drives.

---

### Post by Belfagor on 2006-02-20
i have used debs from debian pool.. may it be the reason? and here is the aoutput....> belfagor@ubuntu:~$ beagle-info --status
Scheduler:
Count: 0
Status: Waiting for the next trigger time

Pending Tasks:
Scheduler queue is empty.

Future Tasks:
Maintenance 0 (02/20/2006 11:33:41)
Optimize MailIndex
Hold until 02/20/2006 11:43:41

Maintenance 0 (02/20/2006 11:33:41)
Optimize KMailIndex
Hold until 02/20/2006 11:43:41

Maintenance 0 (02/20/2006 11:33:41)
Optimize FileSystemIndex
Hold until 02/20/2006 11:43:41

Maintenance 0 (02/20/2006 11:33:42)
Optimize GaimLogIndex
Hold until 02/20/2006 11:43:42

Maintenance 0 (02/20/2006 11:33:42)
Optimize IndexingServiceIndex
Hold until 02/20/2006 11:43:42

Maintenance 0 (02/20/2006 11:33:42)
Optimize TomboyIndex
Hold until 02/20/2006 11:43:42

Maintenance 0 (02/20/2006 11:33:42)
Optimize BlamIndex
Hold until 02/20/2006 11:43:42

Maintenance 0 (02/20/2006 11:33:42)
Optimize LifereaIndex
Hold until 02/20/2006 11:43:42

Maintenance 0 (02/20/2006 11:33:42)
Optimize AkregatorIndex
Hold until 02/20/2006 11:43:42

Maintenance 0 (02/20/2006 11:33:42)
Optimize KonqHistoryIndex
Hold until 02/20/2006 11:43:42

Maintenance 0 (02/20/2006 11:33:42)
Optimize KopeteIndex
Hold until 02/20/2006 11:43:42


---

### Post by RAOF on 2006-02-20
Hm.  Don't know, sorry.  That looks like it's finished indexing, so you should be able to search for files on your vfat drives.  As far as I know, beagle only cares about the filesystem for extended-attributes, and has a fallback system when they're not available.  I don't see why it shouldn't index your vfat partition.

---

### Post by Vurdak829 on 2006-05-06
Same problem here :(

---

