---
title: "Dual Boot Setup"
date: 2009-02-10
forum: General Help
---

### Post by gavinjb on 2009-02-10
Hi,

I am looking at setting up my Laptop to dual boot with Windows XP & Ubuntu, but have a couple of setup questions relating to how I am planning to (hopefully) set it up.

My Proposed Setup is as follows on a 250GB HD

1. Windows XP - NTFS (40GB)
2. Linux Swap (1-2GB)
3. Linux / - Ext3 (15-20GB)
4. Data (Rest)

With Data what I would ideally like to set it up in a way so that from Linux is mounted as /Home and available for users data and in Windows I would map My Documents to the same place so that all data is easily available whether in Linux or Windows, my concerns with this are as follows

1. How to do this in Linux (the MyDocs part in WinXP is easy)
2. What Type to format the drive (I would prefer Ext3, but Win can't read this so looks like Fat or NTFS and NTFS looks the better choice)

Any additional comments would be appreciated on this setup.

Thanks,



Gavin,

---

### Post by ajgreeny on 2009-02-10
You need to have winXP installed first and then, using gparted from the ubuntu liveCD, set up all the partitions for everything, including the one you want as data with "My Documents" in it.  That should be ntfs, as you thought.

Now install ubuntu and choose "Manual" at partitioning.  Set the previously made 15-20GB partition as /, or root, and the one you set for swap as swap, and the data partition should be /home; just ensure that the box for "format" is not checked at that point, or all your data will be gone.  As far as I'm aware it will not matter that it is an ntfs partition for /home, though it is normally ext3, of course, but others may disagree on this point, so wait for more info.

Another way to do the installation is to have a smaller /home for ubuntu, and make yet another partition which you set to mount at ubuntu's boot time, and which you use as "data" but separate from /home.  This way all your configurations and things that are not needed as data files, but are your hidden (in ubuntu) system information files etc, will be in /home, but your docs, photos, music, videos etc etc will be in "data"  This way "data" can be ntfs with no problem, and readable and writable by both OSs, and /home can be its normal ext3 filesystem.  This may well be the better of the two ways to do what you want.

---

### Post by bodhi.zazen on 2009-02-10
You should not use either FAT or NTFS for /home as neither partition supports linux permissions.

Your options are to use ext3, which can be mounted in windows :

[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

A better option may be to use NTFS and rather then mounting it as /home make a link.

for example, mount it in /media/data and then

ln -s /media/data ~/data

---

### Post by mozkill on 2009-02-10
Once you have XP installed, make yourself a backup image of the system using [COLOR="Red"]Clonezilla[/COLOR] (backup the drive image up to a network neighborhood (samba) share on your network OR to your spare hard drive)   then  if something goes wrong during the linux install you will be able to easily recover and try again.

---

### Post by ajgreeny on 2009-02-11
Thanks bodhi.zazen, I had not thought at all about permissions, stupid me.  I should have sat back and thought a bit more before jumping in with both feet.

Just to increase my knowledge of linux, however, what would have happened if the OP had used an ntfs partition as home;  would the system not have recognised it properly as /home, because some of the files and folders need to be not readable by others, etc etc, or would it have worked, but worked badly?

---

### Post by bodhi.zazen on 2009-02-11
> **ajgreeny said:**
> Thanks bodhi.zazen, I had not thought at all about permissions, stupid me.  I should have sat back and thought a bit more before jumping in with both feet.

Just to increase my knowledge of linux, however, what would have happened if the OP had used an ntfs partition as home;  would the system not have recognised it properly as /home, because some of the files and folders need to be not readable by others, etc etc, or would it have worked, but worked badly?

It would semi-work. All the files / directories on the partition would be assigned the same ownership and permissions (as you know these are set at the time of mounting).

So either everything would be owned by root.root or root.users or user1.user1, etc.

If one has more then 1 user, I think the issue is then obvious, the second user will not own his or her own home.

The permissions get more interesting and in the config or dot files you will almost certainly have issues. The ~/.ssh and .drmc  are the two that come to mind :

[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

With the new private home / encryption one may also have issues ...

---

### Post by ajgreeny on 2009-02-12
Thanks for that detail.  I will certainly not forget that again (I hope).

---

