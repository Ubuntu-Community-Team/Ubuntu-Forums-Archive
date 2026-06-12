---
title: "[SOLVED] Moving /home procedural ?"
date: 2008-07-06
forum: Desktop Environments
---

### Post by Barriehie on 2008-07-06
I've seen many threads on the advantages of having **/home** somewhere other than where the default installation creates it so,  I'm almost there but would appreciate clarification!

I've created a partition on a secondary drive, **/dev/hdb2**, and this is where I want my new home partition.   So now I copy **EVERY** file in my current **/home/barrie** directory to **/dev/hdb2** and then add this to **fstab**.

```

/dev/hdb2 /home ext3 nodev,nosuid 0 2

```All this of course after completely backing up my current /home directory.  Hmm, I probably need to recreate the folder structure /home/barrie on /dev/hdb1 also, correct?

---

### Post by HalPomeranz on 2008-07-06
These commands will create a file system in /dev/hdb1 and then copy the contents of your /home directory structure into this file system.

```

sudo mkfs /dev/hdb1
sudo mount /dev/hdb1 /mnt
sudo rsync -avH /home/ /mnt/
sudo umount /mnt

```

The entry you want to put into your /etc/fstab file is:

```

/dev/hdb1  /home  ext3  rw,nosuid,nodev  0 2

```

At this point you should be able to "sudo mount /home" or reboot your machine and have your new home partition mount automatically.

Note that the original files will still be sitting in your "old" home directory, but you won't be able to get at them because the new home partition is mounted on top of this directory.  So at some point you'll want to recover the disk space by doing something like:

```

df -h /home
sudo umount /home
df -h /home
rm -rf /home/barrie
sudo mount /home

```

I included the "df" commands above so that you will BE VERY SURE you that the first "umount" command works before executing the "rm" command.  The output of the two "df" commands should be different-- if it's not then STOP and DO NOT execute the "rm" command.

---

### Post by Barriehie on 2008-07-06
Thank you so far!  I've rebooted and the system is using /dev/hdb2 as the new /home, so far so good.  Then I tried:

```

df -h /home
sudo umount /home
df -h /home
rm -rf /home/barrie
sudo mount /home
```

and I couldn't umount /home; system said it was busy.  This made sense since it was mounted as /home.  So now I've got to login as root and remove **/home/barrie** from **/dev/hda1**, old /home mountpoint to remove the duplication of the files, correct?

Barrie

---

### Post by HalPomeranz on 2008-07-06
> **Barriehie said:**
> The output of the two df commands will be different because the first will show both /homes and the second will show only the current, mounted one, right?

The first df will show you the infomation about /dev/hdb1.  The second will show you information about the original /home directory-- probably part of your root file system on /dev/hda someplace.

---

### Post by Barriehie on 2008-07-06
Alright then HalPomeranz, many thanks to you and your prompt response.  All is well with my /home directory residing on a completely different drive!  Not being extremely eager to rm -rf anything I booted from the LiveCD and renamed /home/barrie on /dev/hda1 to /home/barre.old-home and then booted without the LiveCD.  Everything is intact!

Barrie

---

