---
title: "Permissions on Partition"
date: 2006-09-21
forum: Desktop Environments
---

### Post by msandersen on 2006-09-21
Is there a Wikidoc or something that explains permissions on a mounted partition?
I've recently set up Ubuntu on a machine that used to have Mandrake. I backed up the old Home dir to a partition called Data. I've recursively chowned it to myself.
Ubuntu installed fine with a default fstab entry:
```
/dev/hdb6       /media/Data     ext3    defaults   0       2
```
Now, why can't I write to it as normal user, but only as Root? Not even the root of the partition, let alone the subfolders of the backup, which are owned by me and in my group.
If I right-click on it under Computer and choose Properties, it does say it's owned by Root, but that may be normal for all I know.

---

### Post by kidders on 2006-09-21
How very odd!

So, your ext3 filesystem is mounted during boot and contains files owned by you that the system refuses to let you write to? The first thought that crosses my mind is that the filesystem may be damaged, and is being mounted read-only to prevent further corruption. Check your dmesg and the output of "mount"!

I hope this turns out to be something simple!

---

### Post by msandersen on 2006-09-21
It only refuses the regular user, not if I write as Root, or copy to it as Root. It was freshly formatted before copying over the old Home dir data from another drive during partition reorganisation. The files were originally copied over using a LiveCD before Ubuntu was installed and chowned afterwards.
dmesg doesn't tell me anything. ***dmesg | grep hdb6*** gets
```
[17179579.832000]  hdb: hdb1 hdb2 < hdb5 hdb6 hdb7 >
[17179669.688000] EXT3 FS on hdb6, internal journal
[17209094.692000] EXT3 FS on hdb6, internal journal
```
Mount doesn't complain. 
Opening Gedit as Root and saving a blank document to */media/Data* works, but opening it normally and saving gets a Permissions error. Existing files open fine.
However, saving to the chowned folders are OK. Just not to the root of the partition.

---

### Post by kidders on 2006-09-21
You're sure you don't just need to chmod a few things? Are you certain that **ls -ld /media/Data** shows you a permissions set that would let a normal user write there?

(I'm scouring my brain for something more constructive to say! Damn!)

---

### Post by msandersen on 2006-09-21
I didn't think it would work, but I tried
```
sudo chmod g+w /media/Data
```
makes no difference. I though permissions was all controlled from *fstab*. Permissions now read
```
drwxrwxr-x 8 root root 4096 2006-09-13 13:43 Data
```

---

### Post by msandersen on 2006-09-21
```
sudo chown root:admin /media/Data
```
worked! since I'm part of the Admin group. Wonder why Dapper was set up this way. Something to do with an existing partition originally having files owned by Root?

---

### Post by msandersen on 2006-09-21
Something still not quite right. Nautilus lets me copy to the root of Data now, but greys out options for Create Folder or Paste (when having Copied a file from Home first). Normally it should only do that when you have no permissions. Maybe it will right itself on next reboot. I remounted it just in case.

---

### Post by kidders on 2006-09-21
Its starting to sound like you don't quite understand Linux's permissions scheme. To be allowed to modify something you own, you need to chmod u+w it. Naturally, rebooting has no effect on what you're allowed to do. If you don't own something, or aren't in the group that owns it, you won't normally be allowed to do much more than read it.

To find out what groups you're in, just type "groups".

**Edit:** Take a look at the files you want to change with "ls". If you don't understand what the d, r, w, x, s, t, etc. symbols down the left hand side are, I can explain.

Hope that helps :-)

---

### Post by msandersen on 2006-09-21
Just though it could be a bug in Gnome, sometimes these things go away on reboot/X restart. Even if I set ownership to martin:admin with permissions drwxrwxr-x, though I can copy to it now, Nautilus doesn't show paste/Create Folder/Create Document options for Data.

---

### Post by Omnios on 2006-09-21
Hi in my signature there is a fstab link to tuxfiles that has a indepth acticle on how fstab works and even permitions etc. 

 Currently I have used this entry for over a year which seems to work.
```

/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0

```

---

### Post by kidders on 2006-09-21
> **msandersen said:**
> Just though it could be a bug in Gnome, sometimes these things go away on reboot/X restart. Even if I set ownership to martin:admin with permissions drwxrwxr-x, though I can copy to it now, Nautilus doesn't show paste/Create Folder/Create Document options for Data.

Hmm... It could be a bug, I guess. I wonder if Gnome's bug databases have reports of anything similar.

---

### Post by kidders on 2006-09-21
> **Omnios said:**
> Hi in my signature there is a fstab link to tuxfiles that has a indepth acticle on how fstab works and even permitions etc. 

 Currently I have used this entry for over a year which seems to work.
```

/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0

```

Wow! I guess you're not too concerned about security. I bet it works great though :-)

---

### Post by msandersen on 2006-09-22
> **Omnios said:**
> Hi in my signature there is a fstab link to tuxfiles that has a indepth acticle on how fstab works and even permitions etc. 

 Currently I have used this entry for over a year which seems to work.
```

/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0
```
I think that's what got me confused, because I'd experimented with the NTFS-3G driver, and NTFS-Fuse before it, on another computer. It worked great. Never had to touch the ext3 partitions, as there were no problems.
So I read about the options for it, and set it to my gid and uid with appropriate umask. I tried it here for the ext3 partition, but got errors, hence my question about a link to how to set permissions, as I though it might have been fstab-related. With ntfs-3G/ntfs-fuse, it didn't matter what the folder permissions were, Fuse sets the mounted permissions based on the fstab options.
I found a link to the same article on a different site (I think) after posting, so realise now there's nothing in the Options to set permissions for the mounted volume. I guess it's because NTFS is a foreign file system with a different permissions system, hence it sets default permissions/ownership in fstab.

---

### Post by kidders on 2006-09-22
Yep, trying to override an extended filesystem's permissions won't work ... it would violate the whole principle of security, I suppose. The only reason mount supports this feature for FAT and NTFS is because their access control features are crap.

---

### Post by msandersen on 2006-09-23
Just for the record, now that I've restarted, the options for Create Folder, Paste etc are back for the Data partition, so all is as it should be. Thanks.

---

