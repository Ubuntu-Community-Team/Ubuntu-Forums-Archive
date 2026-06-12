---
title: "Mounting HD"
date: 2009-01-21
forum: General Help
---

### Post by doubad on 2009-01-21
Alright, so my computer has 3HD's.
1 250gb sata2 ext 3that has ubuntu
1 250gb sata2 ntfs for storage
and 1 40 gb ide that i usually keep xp on for games etc. (rarely used)

I decided for fun to try the windows7 beta on the 40gb and the setup screwed up and dind't work.
That drive basicaly doesn't work anymore, I can't seem to get anything on it anymore. Ubuntu couldn't put a ext3 system on it. No big deal, I don't really need it anymore anyways so I unplugged it.

What's really getting to me is that my 250gb storage drive can't be mounted anymore, I no longer have access to it. It's still full of files since it says how much space is used/free. It shouldn't have been touched or affected during the install. Not sure what's going on. The Ubuntu drive works as usual. Any tips for getting ubuntu to reconize my storage drive again?

I vow to never touch windows again, this may get costly :(

---

### Post by cdtech on 2009-01-21
Make sure you can see it using:
```
sudo fdisk -l
```
then edit your "/etc/fstab" file to include the device (/dev/sd?) rather than the UUID. It may need to be updated (UUID). Use "blkid" to find it if you'd rather use the ID.

---

### Post by jerome1232 on 2009-01-21
I think issueing a mount command should give us a good error message to go off of.

This command should walk through your fstab and try to mount anything that isn't already mounted. And hopefully give us an error message.
```
sudo mount -a
```

---

### Post by drs305 on 2009-01-21
If you aren't able to mount it via the previous replies:

Is this an ntfs partition? If so, an unclean shutdown may be responsible. It sounds like you can't, but if you can the preferred method is to get back into windows and do a normal unmount/shutdown of the device.

If you can't do that, you can install ntfsprogs and run ntfsfix on the partition. It should resolve the issue. Of course, any time you are dealing with non-native partitions you should back up your data. Standard disclaimer, I know you can't in this case.

Install ntfsprogs:
```

sudo apt-get ntfsprogs

```

To run:
```

sudo ntfsfix /dev/sd**XX**

```

---

### Post by doubad on 2009-01-21
> **jerome1232 said:**
> I think issueing a mount command should give us a good error message to go off of.

This command should walk through your fstab and try to mount anything that isn't already mounted. And hopefully give us an error message.
```
sudo mount -a
```


Sweet, it worked.

```
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/Windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/Windows ntfs-3g force 0 0

```

 I then selected Choice 2 and all is well.

Thanks!!

---

