---
title: "How to move /home from old to new drive"
date: 2013-02-14
forum: Desktop Environments
---

### Post by JB1234 on 2013-02-14
Hello,

My daughters desktop (Ubuntu 12.10) has the following disk config:

32GB SSD - boot & system partitions
160GB HDD - /home

She's running low on space so I bought her a new 500GB HDD to replace the 160GB drive, my question is this, is their an easy way to move /home from the old disk to the new disk without reinstalling everything? 

To clarify, the 160GB disk is almost 6 years old so will be 'retired' after the move, and /home is to use the whole 500GB of the new drive.

I spent a while Googling this but most of the results were very outdated and not really what I was looking for.

Thanks in advance,

John

---

### Post by nwalkey on 2013-02-14
Might work to just copy everything in the /home drive to the other drive. You might be able to drag and drop or mount both drives and do 'cp /home/* /whatevermountpointfornewdriveis' . Then just make sure /etc/fstab is setup right to use the new drive as /home. Probably the quickest and easiest way I can think of. You can then repurpose the old drive or recycle it. Hope that helps.

---

### Post by schragge on 2013-02-14
Provided that the new disk (say /dev/sdc1) is already formatted (e.g. mkfs.ext4 for ext4 filesystem), you can do this:
```

sudo mount /dev/sdc1 /mnt
sudo mkdir /mnt/[COLOR=green]user[/COLOR]
sudo chown [COLOR=green]user[/COLOR]: /mnt/[COLOR=green]user[/COLOR]
cd /home/[COLOR=green]user[/COLOR]
tar cf - . | (cd /mnt/[COLOR=green]user[/COLOR] && tar xpBf -)

``` where [COLOR=green]user[/COLOR] is the username of your daughter.

---

### Post by oldfred on 2013-02-14
I prefer rsync. But these are all really the same just using different copy commands.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses sudo cp -ax * /mnt/newhome where the -ax preserves parameters
[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

    
If you create a new partition it will have a new UUID and you will have to update fstab with the new UUID.

---

### Post by JB1234 on 2013-02-19
Thanks for the replies :)

I'm still considering my options but I'll be changing the drives over tomorrow so will post an update then, thanks again!

John

---

