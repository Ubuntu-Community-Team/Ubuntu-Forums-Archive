---
title: "Naming USB meory stick"
date: 2009-11-02
forum: Florida Team - US
---

### Post by a2z on 2009-11-02
Hi everyone,
I've come to this forum not knowing any better where else to put this question. 
I've read some replies as to naming usb sticks/thumb drives.
Some say you can't name them. And in my little experience with linux (since jan.09) have not been able to find a way to do it.

If this is the case with linux, I would just about expect a remedy for this. Mostly because I can name sticks in windows and the naming is preserved when passed over to ubuntu.
And I also know what ever you can do in windows, you can do with linux and probably better.

Anyone know how to name usb drives.
I'm using ubuntu jaunty. I have tried karmic beta about 3 weeks prior to final release. Liked it for the most part, but for me, continually went south.
Thanks for any and all input,
a2z

---

### Post by squaregoldfish on 2009-11-02
I'm pretty sure you can do this with GPartEd - the disk partitioning tool. Just be careful with it!

Steve.

---

### Post by a2z on 2009-11-02
> **squaregoldfish said:**
> I'm pretty sure you can do this with GPartEd - the disk partitioning tool. Just be careful with it!

Steve.

This is good news. 

Thanks, I hope it works

a2z

---

### Post by itnet7 on 2009-11-02
You can also do this while formatting the partition using fdisk.

$ sudo mkfs.vfat -F 16 -n liveusb /dev/sdb1

The label would be livusb in the above example.

Or if you already have a partition you can follow [this guide]("https://help.ubuntu.com/community/RenameUSBDrive#Changing%20the%20Label") for both gparted and CLI.


I did the following on my usb-thumbdrive

```
sudo mlabel -i /dev/sdb1 -s ::
```

And received the following:

Total number of sectors (1973410) not a multiple of sectors per track (61)!
Add mtools_skip_check=1 to your .mtoolsrc file to skip this test

Then I added this: 

```
echo mtools_skip_check=1 >> ~/.mtoolsrc
```

and re-ran the previous command:

```
sudo mlabel -i /dev/sdb1 -s ::
``` 

This time it showed me this:  

```
Volume has no label
```

I edited the following: 

```
sudo nano /etc/mtools.conf
```

and added this line to the end of the .conf file. 

```
drive p: file="/dev/sdb1"
```

and saved my changes. 

```
sudo mlabel p:usb-ubuntu
```

then ran the following again: 

```
sudo mlabel -i /dev/sdb1 -s ::
```

and saw this:

```
Volume label is USB-UBUNTU
```

I just did this on Karmic without any troubles.

Hope this helps!

Chris Crisafulli
itnet7/irc.freenode.net
Ubuntu Florida Team

---

