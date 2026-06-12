---
title: "Mounting Help"
date: 2009-02-16
forum: General Help
---

### Post by Dr Zin on 2009-02-16
I am needing to move my home directory to a another drive. I thought could find a simple application that could this for me, but I couldn't. so what is the command to do this? 

The real issue I seem to running out of space and I am getting different readings form different applications on the my space of my hard drive. I have two 250 GB death stars and one 60 GB 2.5 drive. I am little issue with disk space management.

---

### Post by dzark on 2009-02-16
Open up gParted ("System -> Admin -> Partition Editor") 

and create a new partition on another drive...

then set its mountpoint as /home...

---

### Post by yther on 2009-02-16
You can copy all of your files by doing this:

```
sudo mkdir /mnt/newhome 
sudo mount /dev/whatever /mnt/newhome
sudo mkdir /mnt/newhome/yourusername
sudo chown yourusername /mnt/newhome/yourusername
cp -a ~/ /mnt/newhome/yourusername/
```

Then after that, you'd edit /etc/fstab to mount the new drive where /home was before, and restart (well, you don't have to reboot, but it's probably easier that way).  Note that if /home was previously just a directory, you should rename it first, otherwise mounting something on top of it will cause its contents to seem to disappear!  :)

---

### Post by Dr Zin on 2009-02-16
> **yther said:**
> You can copy all of your files by doing this:

```
sudo mkdir /mnt/newhome 
sudo mount /dev/whatever /mnt/newhome
sudo mkdir /mnt/newhome/yourusername
sudo chown yourusername /mnt/newhome/yourusername
cp -a ~/ /mnt/newhome/yourusername/
```



I this might be a little stupid. But could just name that dir /home?

---

### Post by yther on 2009-02-17
Well, sure.  Of course you can name the directory in /mnt whatever you like; I'd do something like the above just because it makes sense to me.  :)  That sort of assumes that you're going to be using the entire new drive as your /home from now on, and that you currently have stuff in /home (files, settings, etc.) that you want to keep.

If your current /home is on a partition or drive of its own, all you'd really have to do is copy your files to the new one, then change the mount points and reboot.

---

### Post by Dr Zin on 2009-02-17
ok thank you for your help.  I am have one more issue. That is the I was able to open the fstab file up and then completely I was lost.```

proc            /proc           proc    defaults        0       0
UUID=173933a8-5e4d-4010-8b6d-aff50e3cf0a4 /               ext3    relatime,errors=remount-ro 0       1
UUID=a46c5294-6a72-4848-a170-5034bd2f1423 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by yther on 2009-02-17
I'm not surprised!  The contents of that file look very intimidating—and maybe that's good, because a mistake in that file can prevent your system from starting!  :shock:

/etc/fstab is the "master" file that tells your system what disks (and things that act like them) you have, and where to put them.

Have a look at the [Community docs page on fstab]("https://help.ubuntu.com/community/Fstab"), and you can also type "man:fstab" in Konqueror for the official documentation (that one is probably harder to read, but it should have very complete information, and may also be translated to your local language if that isn't English).  The Ubuntu page should be a good starting point for you, if you want to know the basics and more.

Now, if the lines you posted are your *entire* fstab, it says you have everything in one partition.  That is, /home is just a "folder" like any other.  You are going to put /home on a new drive, so you will need to state that in the **fstab**.  (Unlike in Windows, you have a lot of flexibility when adding a drive to your system.  It doesn't have to go into the top level, so you can mount it anywhere you like.)  For example, mine has this:

```
# /dev/sda8
UUID=e407b24d-b891-47f3-93a3-ca62784bcc51 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f2aa95bd-b678-4a84-bc91-15c7b8985336 /boot           ext2    relatime        0       2
# /dev/sda9
UUID=24e1eb0d-6f51-4ef9-b692-031f4c6de923 /home           ext3    relatime        0       2
# /dev/sda7
UUID=dd109680-93dd-4816-ad96-2e5a8c3396c0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda10      /vault          ext3            relatime,noexec 0       2
/dev/sda3       /mnt/Vista      ntfs    noexec  0 0
```

The last two lines don't use UUIDs because I was lazy and didn't bother finding them.  You would need to *add* a line for your /home similar to this.

So after looking at the docs and this post, are you getting close to what you need to do?  :)

---

