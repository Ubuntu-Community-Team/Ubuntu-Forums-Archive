---
title: "upgrade, saving home directory"
date: 2009-02-08
forum: General Help
---

### Post by nbo10 on 2009-02-08
Hi All,
I need to do a fresh install from 7.10 to 8.10. Is there a way to just transfer my home directory over to the new system? I want to keep all my emails and stuff.

Is there a file with all the packages installed, on 7.10. oh yeah, I can't boot into 7.10 that's why I have to reinstall.

---

### Post by earobinson on 2009-02-08
using the live cd you should be able to mount the drive you originaly installed ubuntu on and copy your home drive off, (the live cd may also offer to transfer your files but its always best to manualy bacup)

As for your second question... I dont think so.

---

### Post by mb_webguy on 2009-02-08
Use Archive Manager to create a tarball of your home directory, specifically all of the hidden configuration files and folders.  Tarballs maintain file permissions, which is important for transferring your config files.  It doesn't really matter what compression method you use.  Save the tarball to an external storage device, like a USB flash drive.

Now install the new version of Ubuntu.  I suggest creating a separate /home partition so you don't have to go through this again.  Once you've rebooted and logged in to your new account, plug in the external storage where you saved the tarball, and extract it to your new home directory, overwriting the existing files.  If you changed your username, you'll have to change the owner of the files using the command "find ~/ -user *old_username* -exec sudo chown *new_username*:*new_usergroup* {}".  (I'm about 95% sure about that command, but you may want to check it on a test directory first.)  Once you logout and log back in, you'll be using your old config files.

As for packages installed, once you have restored your config files, all of the applications you had previously installed will show up in your Applications menu.  Just go down the list installing the missing apps.  This won't help you with any CLI apps you had installed, but it's a good start.

---

### Post by nbo10 on 2009-02-09
Okay, I'm trying to make a tarball of my home dir but I'm getting an error

I'm booting with the live cd. I've tried two ways of creating the tarball. One with gksudo file-roller after I click on my home folder to add to the archive I get
```
An error occurred while adding files to the archive.  No such file or directory 
```

If I open  gksudo nautilus and right click on my home dir and create an archive I get the same error.


I need help asap. Thanks

---

### Post by nbo10 on 2009-02-09
Will the tar command from a terminal copy all the hidden config files? Thanks

---

### Post by geirha on 2009-02-09
> **nbo10 said:**
> Will the tar command from a terminal copy all the hidden config files? Thanks

Yes. Assuming you've mounted your linux partition at /media/disk/:
```

cd /media/disk/

# This will archive all home directories, including all the hidden 
# files, preserving ownership, permissions and timestamps.
sudo tar zcvf /place/to/store/archive.tar.gz home/

```

To get a list of all packages installed, you can try to chroot into your partition (from the liveCD), and run dpkg --get-selections:
```
sudo chroot /media/disk/
dpkg --get-selections > ~/Desktop/packages.txt

```

---

### Post by grndslm on 2009-02-09
It's always possible to upgrade multiple distributions or OSes if you keep your /home folder in its own partition.  Then there's no need to tar, move, untar, move some more, etc...

---

### Post by nbo10 on 2009-02-09
> **grndslm said:**
> It's always possible to upgrade multiple distributions or OSes if you keep your /home folder in its own partition.  Then there's no need to tar, move, untar, move some more, etc...

Well, Now I know that.

What size does the root directory need to be for 8.10. I have a 100GB harddrive, I'll put my home dir in another partition.

---

### Post by mb_webguy on 2009-02-09
If you're not dual-booting, then you can just have an 8-12GB partition for the / partition, a swap partition equal in size to your system memory, and the remainder of the drive as your /home partition.

If you're dual-booting, especially with Windows, then you probably want to keep your /home partition and data partitions separate.  Since in this case the majority of your files would be somewhere else, your /home directory could be just a couple of GB.

---

### Post by Slim Odds on 2009-02-09
> **mb_webguy said:**
> If you're not dual-booting, then you can just have an 8-12GB partition for the / partition, a swap partition equal in size to your system memory, and the remainder of the drive as your /home partition.

It depends on how you intend to use it.

For example: some DVD creation program might want to create an image file on the fly. That means that it might want up to 8.5 GB (in the case of DL) of space in /tmp

If you have a single partition for /, and everthing else except /home is there, then you'll be out of space in no time.

On my system, I have a 14G /tmp partition.

Just remember, if you don't put it somewhere else, it goes in /

---

