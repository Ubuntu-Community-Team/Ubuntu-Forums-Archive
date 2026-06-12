---
title: "Help renaming software raid5, operation not supported by back end ?"
date: 2008-12-08
forum: General Help
---

### Post by Sullr on 2008-12-08
hi,

I have setup a software raid 5 in Ubuntu 8.10 using hdadm,  but I cannot seem to rename the drive listed in nautilus, reads 1000.2 GB Media and when I try and rename I get this message 

> The item could not be renamed.

Sorry, could not rename "1000.2 GB Media" to RAID5-1T":Operation not supported by backend


I looked at some of the conf files to see if I could find the name of the drive, but have been unsuccessful, maybe can someone point me in the right direction in renaming this raid ):P

Thanks

---

### Post by fjgaude on 2008-12-08
I'm not sure what you are trying to achieve. The raid was named something like /dev/md0 when it was created. You can mount it to a point with the name you wish, like:

```
sudo mkdir /RAID5-1T
```

and then mount it there, like:

```
sudo mount /dev/md0 /RAID5-1T
```

In your /etc/fstab file you would add this line:

```
/dev/md0   /RAID-1T   ext3   defaults   0   2
```

Of course you can call the mountpoint anything you wish and have it anywhere else, just giving as example here.

Let us know if you need anything else, how you are doing.

---

### Post by Sullr on 2008-12-08
Sorry I was not clear enough!


```
/dev/md0   /RAID5-1T   ext3   defaults 0 3
```

That is what my fstab looks like and the drive is automatically mounted when I startup, but in nautilus the drive is listed as "1000.2 GB Media" and I cannot rename it....

In nautilus I just want the drive to be named "RAID5-1T" ...

Does this make sense now ?

---

### Post by fjgaude on 2008-12-08
Okay, if you change to Tree in Nautalus, the left panel, you will see the /RAID5 as a partition.

If you made a mountpoint at /home/RAID5 then you would see it as a sub partition under /home.

Now I just thought of another way that might do you: label the array!

```
sudo e2label /dev/md0 RAID5
```

Using tune2fs -L will do it also. Have to read the man pages to recall.

I think this might be what you are looking for.

---

### Post by Sullr on 2008-12-09
Thanks, I am just in the middle of fixing my system so soon as it's up and running I will try that.

I'll let you know if that does it.

Thanks alot

---

### Post by fjgaude on 2008-12-09
Okay, do let us know how it goes. Here's the man paragraph for the -L option of **tune2fs**:

>       -L volume-label
              Set  the volume label of the filesystem.  Ext2 filesystem labels
              can be at most 16 characters long;  if  volume-label  is  longer
              than  16  characters, tune2fs will truncate it and print a warn&#8208;
              ing.  The volume label can be used  by  mount(8),  fsck(8),  and
              /etc/fstab(5)  (and  possibly  others)  by specifying LABEL=vol&#8208;
              ume_label instead of a block special device name like /dev/hda5.

So the command to give a name to a drive or array would be:

```
sudo tune2fs -L RAID5-1T
```

in you case. Then in the fstab file you would have LABEL=RAID5-1T instead of /dev/md0.

Good luck.

---

### Post by Sullr on 2008-12-09
K my machine is up and running again!

Yes it worked perfectly :)

```
sudo e2label /dev/md0 RAID5-1T
```

Then 

```
sudo gedit /etc/fstab
```


Change the line 

```
/dev/md0
```

to

```
LABEL=RAID5-1T
```

Now the name shows up as RAID5-1T in nautilus.. for anyone else who wants to rename software raid!


Thanks for all the help fjgaude

---

### Post by fjgaude on 2008-12-09
You are more than welcome! Enjoy!

---

