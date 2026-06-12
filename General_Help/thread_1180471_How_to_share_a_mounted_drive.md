---
title: "How to share a mounted drive"
date: 2009-06-06
forum: General Help
---

### Post by CrazeDIzzleD on 2009-06-06
Okay, so here is my situation. I have 3 hard drives some with several partitions. One partition on one of my drives is for Ubuntu, the rest are NTFS for Windows. I have a 500GB NTFS drive that holds all of my music and movies. While in Windows, this drive is shared to my network so other people in my house can access my music and movies.

Right now I have this drive mounted in Ubuntu to /media/downloads. I want to share this drive to my network just like I do in Windows, but how do I do that? I successfully shared a different folder and a Windows computer can access it, but when I try to share /media/downloads (via rightclick>Sharing Options) I get this error:

> 'net usershare' returned error 255: net usershare add: cannot share path /media/Downloads as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this

So I guess I have to add a line to smb.conf. Where do I find the smb.conf I need to edit? Doing a file search yields several smb.conf with similar contents so, which one do I edit?

Thanks.

---

### Post by sigixv on 2009-06-07
you can share it as root

```
sudo nautilus
```

cd to the directory and set the share options it as you would otherwise

---

### Post by colau on 2009-06-07
> **CrazeDIzzleD said:**
> Okay, so here is my situation. I have 3 hard drives some with several partitions. One partition on one of my drives is for Ubuntu, the rest are NTFS for Windows. I have a 500GB NTFS drive that holds all of my music and movies. While in Windows, this drive is shared to my network so other people in my house can access my music and movies.

Right now I have this drive mounted in Ubuntu to /media/downloads. I want to share this drive to my network just like I do in Windows, but how do I do that? I successfully shared a different folder and a Windows computer can access it, but when I try to share /media/downloads (via rightclick>Sharing Options) I get this error:



So I guess I have to add a line to smb.conf. Where do I find the smb.conf I need to edit? Doing a file search yields several smb.conf with similar contents so, which one do I edit?

Thanks.
/etc/samba/smb.conf
Does this help?
[samba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by CrazeDIzzleD on 2009-06-10
Thanks, that worked.

Now how do I change permissions so they can only read the files but not modify them? I tried using chmod but it didn't appear to change the permissions on any of the files...

EDIT: Dee da dee, that was part of the sharing options. xD

I'm all set now. Thanks for the help.

---

### Post by blueridgedog on 2009-06-10
> **CrazeDIzzleD said:**
> 
Now how do I change permissions so they can only read the files but not modify them? I tried using chmod but it didn't appear to change the permissions on any of the files...

Keep in mind that non Linux files systems can have detailed permissions set.  For fat/fat32/ntfs they are mounted as a given user and have a given set of permission on mount.  Chmod/Chown only works on ext2/3/4 systems.  

LS will show owner, group and permissions, but they are based on the mount command, not on the files.

---

### Post by kdla1957 on 2009-06-19
Blueridgedog, - From what I gather, The NTFS permissions on the files and folders of my second hard drive is what is preventing me from sharing a folder on that drive - hence the error message "cannot share path /media/Sweetest/movies as we are restricted to only sharing directories we own."
How do I get past that? Before I installed Ubuntu, I could share that drive with other computers in my home. I'd like to regain that functionality.

What if I move all the files to another drive (make a backup) and use Ubuntu to format /media/sweetest, then move the files back?

I'm not disappointed in taking this "leap of faith" from Windows, I expected to be a little inconvenienced for a short while. Much to learn

---

### Post by blueridgedog on 2009-06-21
> **kdla1957 said:**
> From what I gather, The NTFS permissions on the files and folders of my second hard drive is what is preventing me from sharing a folder on that drive - hence the error message "cannot share path /media/Sweetest/movies as we are restricted to only sharing directories we own."


If you are trying to share the files as a user via the Nautilus GUI, then you need to own them (I think), which means you either need to share the files as the super user (root) by editing the samba configuration file or you need to change where the system mounts the drive, so that it mounts it where you own the mountpoint (a fancy word for the directory name used to attach the drive to your file system).

If you want to solve it from the user perspective, the fist thing I would make certain of is that your user account owned the mount point so you could share it.  Can you share the mount command that you are using the mount the drive?  If it is mounted automatically, then we can fix that by mounting it where you want.

If we assume that is is /dev/sdc1 (which it may not be, but you can verify what drive it s with ```
sudo fdisk -l
or
mount

```

Fist, unmount it:

```
sudo umount /media/sweetest
```

Then make a place for it to reside in the future:
```

mkdir /home/kdla1957/sweetest
```
or 
```
sudo mkdir /mnt/sweetest
chown kdla1957:kdla1957 /mnt/sweetest
```

I doubt kdla1957 is your user name, but you get the idea.  The first command places the mount point in your home directory and the alternative places it in the traditional /mnt structure.  If you are the only user of the system, then your home directory is fine.

Then you can mount the drive from the command line:

```
sudo mount.ntfs-3g /dev/sdc1 /mnt/sweetest 
```

Change /mnt/sweetest to the directory you actually made.

Since you own the mount point, you should be able to share the drive at this point.  If that works, then we set it up so that it mounts it permanently, every time you boot your system.

If it fails to work as expected, we can supply options to the mount command.

> **kdla1957 said:**
> What if I move all the files to another drive (make a backup) and use Ubuntu to format /media/sweetest, then move the files back?


Well, you could do that and remove the NTFS issue, but you would still need to understand how to mount drives and own them so that your user account can act on them - or shift gears and start to work with file sharing from a system perspective.  Even if you did dump NTFS, you would still need to mount the drive in a more permanent (and potentially owned by you) location.

Also, keep in  mind that if you dump the NTFS drive, you will not be able to access your files from within MS Windows.

> **kdla1957 said:**
> I'm not disappointed in taking this "leap of faith" from Windows, I expected to be a little inconvenienced for a short while. Much to learn

I expect that you will get it working.

---

