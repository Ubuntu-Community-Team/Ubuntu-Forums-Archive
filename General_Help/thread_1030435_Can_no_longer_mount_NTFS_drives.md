---
title: "Can no longer mount NTFS drives"
date: 2009-01-04
forum: General Help
---

### Post by test_test_testing on 2009-01-04
Before, I could click on Places > Disk and it would mount successfully, however when I did 'mount LABEL=disk' in the terminal it would say:

> 
Unprivileged user can not mount NTFS block devices using the external FUSE library. Either mount the volume as root, or rebuild NTFS-3G with integrated FUSE support and make it setuid root. Please see more information at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)


I didn't want to mount using root, so I went to [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged) and followed the instructions:

```

  chown root $(which ntfs-3g)
  chmod 4755 $(which ntfs-3g)

```

However, 'mount LABEL=disk' reported:

> 
Mount is denied because setuid and setgid root ntfs-3g is insecure with the external FUSE library. Either remove the setuid/setgid bit from the binary or rebuild NTFS-3G with integrated FUSE support and make it setuid root. Please see more information at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)


So I decided to give up, until I found that now even mounting normally from Places > Disk didn't work. It would report 'Unable to mount the volume 'Disk'.' and when I clicked details, the same error as I quoted above appeared. I tried reinstalling ntfs-3g and libntfs-3g28 to no avail, the message under 'details' was the same as the first quote. Any help would be appreciated.

---

### Post by zeronothing on 2009-01-04
This is how I mount my NTFS drives on my PC. first I find out what all of my drives are listed under using this command interminal:

sudo fdisk -l

this will list all of your drives in the PC. Now after you found out what drive to mount its now time to mount the ntfs volume. first we will need to make a directory to mount the drive to. I usually make the directory somewhere in the /media directory. for example you would use the following command to create the directory:

sudo mkdir /media/harddrive

now that we made the directory we can mount the the ntfs volume in that directory:

sudo ntfs-3g /dev/(disk drive listed under fdisk command) /media/harddrive


this will allow you to mount the ntfs volume under terminal. now if you would like to auto-mount the drive on startup let me know.
hope this helps for the time being.

---

### Post by test_test_testing on 2009-01-04
I understand how to use 'sudo ntfs-3g' and stuff, but what I meant is that I can no longer mount from the places menu. :) I can mount it from sudo ntfs-3g to clarify, but it appears that the places menu doesn't run mount as root. Thanks for the reply anyway.

---

### Post by zeronothing on 2009-01-04
you might want to see if the Fuse config needs to have the "allow_others" not commented out. if you edit the /etc/fuse.conf make sure you uncomment the "allow_others" to see if that helps.

---

### Post by test_test_testing on 2009-01-05
Nope, still nothing... Do I have to reboot after editing fuse.conf?

Otherwise, could somebody pass me a link to a ntfs-3g package built with integrated FUSE support?

---

### Post by SaiHayashi on 2009-03-07
im hitting the same problem, tried all suggestions above but none falls to solution.

---

### Post by martin_lindhe on 2009-12-20
If you have setup ntfs partitions with fstab you must add the "exec" parameter on them in order for wine to work properly

for example:

/dev/disk/by-label/win-games    /media/win-games    ntfs         users,auto,rw,exec            0 9

---

### Post by Antares784 on 2010-08-12
How does one mount this without using sudo? For example, I want to mount this partition at startup in a way that I can have rw-access to it. Whether with NTFS or FAT-32 partitions, if I mount at startup it's always mounted read-only, whereas if I don't, I sometimes try to reference files that are on a partition that hasn't been mounted. Help?

---

### Post by stealthmode linux on 2010-11-24
I wrote this little guide for myself with information from the forum, it might help others as slow as me xD

How to boot mount drives:

Open filesystem/media/ as root and create 
the folders to mount drives to:
 
filesystem/media/ create new folder> drives name

Then open /etc as root and edit fstab or in terminal enter:
 
sudo nano -Bw /etc/fstab 
 
Add the line 
 
/dev/sdb1 /media/disk-1 ntfs defaults 0 0
 
Edit sdb1/c1/d1 required for the drive/partition you want to mount 
(take a peek in disk partitioner for drive info) 
 
ctrl x to save and quit 
*or save in text editor
 
Example fstab additions:

#Mount WINDOWS 80GB  
/dev/sda1 /media/80GB ntfs defaults 0 0
#Mount 300GB MINI DRIVE 
/dev/sdb1 /media/300GB ntfs defaults 0 0
#Mount 120GB MAXTOR
/dev/sdc1 /media/120GB ntfs defaults 0 0

See the post above for additions for WINE, hope this helps somebody :)

---

