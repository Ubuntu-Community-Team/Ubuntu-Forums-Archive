---
title: "NTFS with multiple accounts"
date: 2010-04-24
forum: Desktop Environments
---

### Post by croutonkid94 on 2010-04-24
So I have set up Ubuntu on my parents' computer and made two user accounts; one for me and one for them. At my dad's urging, both are administrator accounts.  His is set for "Automatic Login" (yes, I do know that is rather stupid but he did it on Windows and wants it now).  

Now we have a 320GB external hard drive formatted completely in NTFS and I have used ntfs-config to set it up. When he auto-logs in, it is mounted under /media with him as owner and mode 700. If I then log him out and log in under my account, the folder does not get chown'ed to me and the mode remains 700.  Is there any way to fix this? Thanks in advance.

--Harrison

---

### Post by coffeecat on 2010-04-24
I don't have much experience of ntfs-config (I edit fstab manually for NTFS partitions) but when I did try it, I thought the options field that it set up in fstab unnecessarily complicated. Have a look at the ntfs line it has generated in /etc/fstab and see what it has put in the fourth field. If you need help, post the whole contents of /etc/fstab:

```
cat /etc/fstab
```For NTFS, I find a simple:

```
device    mountpoint    ntfs    defaults    0 0
```... works just fine and that should allow all users to access files OK. (By the way, you can have 'ntfs' or ntfs-3g' in the third field. It makes no difference - the ntfs-3g driver is used either way.) One seeming oddity of mounted NTFS partitions is that all files appear to be owned by root. That's because NTFS doesn't support Linux permissions and user access is determined by the mount options. Hence a simple 'defaults' is probably best. Have a look also at:

[https://help.ubuntu.com/community/Fstab#File%20System%20Specific%20Examples](https://help.ubuntu.com/community/Fstab#File%20System%20Specific%20Examples)

... which simply adds a locale option. 

One other thing to look at is the ownership of whatever folder in /media is being used as the mountpoint. It should be owned by root. If ntfs-config has chowned it to your father's ownership, that might explain part of the problem.

---

### Post by croutonkid94 on 2010-04-25
Thanks for the reply.

This is interesting; there is no line for the device in /etc/fstab.  It shows up in /etc/mtab as:
```
/dev/sdb1 /media/SignatureMini fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

```

Now I'm not great with these types of things but it seems that I need to copy it over to /etc/fstab and remove "default_permissions", possibly.  I am also confused by the filesystem type being specified as "fuseblk", which I'm assuming is some special fs type.  I'll try your line right now.

Thanks,
--Harrison

EDIT: With your line, it mounts fine.  I had to mkdir the target directory, but I seem to have permissions. Thanks!

---

### Post by coffeecat on 2010-04-25
> **croutonkid94 said:**
> EDIT: With your line, it mounts fine.  I had to mkdir the target directory, but I seem to have permissions. Thanks!

Excellent. Using fstab is probably the way to go so long as the external drive is already switched on when you boot up, but a couple of comments and questions.

First - a couple of apologies. My memory of ntfs-config must be a bit awry. :oops: It must be creating dynamic entries in mtab as it goes. Also, I see now that you are mounting an **external** drive formatted NTFS. For some reason I read that last night as an internal partition (it was late) which is why I was thinking of /etc/fstab. But I seemingly managed to get to the right answer for the wrong reason! :|

Out of curiosity, why were you using ntfs-config for an external drive? My memory of ntfs-config was for an internal partition, so perhaps it does modify fstab for them. Anyway, with an external drive udev should take care of automounting an NTFS drive whether already running at bootup or when connected to a running desktop. Out of interest, I tried attaching an external NTFS drive, allowing it be automounted, and then logged out and in again into another (non-admin) account. The drive didn't appear anywhere even though still running, and I had to switch it off and on again for it to be remounted in the new account. Ditto when switching back to my main account. But I was able to access the drive in both accounts. As automounting of external drives comes in the box, so to speak, courtesy of udev, was there a reason for installing ntfs-config?

---

### Post by croutonkid94 on 2010-04-25
Well, the drive was mounting fine, but I couldn't get it to give me write permissions on the drive without being root.  I looked around aptitude and found ntfs-config, which seemed to at least let me write to the drive.  I also have a dual-boot setup, which I originally planned to use ntfs-config for.  Thanks again for the solution.

--Harrison

---

