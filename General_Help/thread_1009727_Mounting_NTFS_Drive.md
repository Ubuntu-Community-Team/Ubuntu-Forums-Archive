---
title: "Mounting NTFS Drive"
date: 2008-12-12
forum: General Help
---

### Post by Audi0Fr3ak on 2008-12-12
First my system...

I have two HDDs, one is 80gb and one is 250gb

the 80gb is soley for ubuntu and the 250gb is all plain storage, NTFS file structure...:( not friendly with my newly installed Ubuntu...

In the error it told me to add this line to my /etc/fstab

/dev/sdb1 /media/Windows Drive ntfs-3g force 0 0

so i did, now my new error is
> 
[mntent]:line 10 in /etc/fstab is bad
mount: can't find /media/Windows in /etc/fstab or /ect/mtab


any help would be great! that server drive has TONS of my stuff... 250gb full of it!:confused:

---

### Post by gettinoriginal on 2008-12-12
I don't have an NTFS drive or Partion, but you might find something to help you here:

[http://lifehacker.com/software/ubuntu/ubuntu-tip--how-to-mount-a-windows-ntfs-partition-203102.php](http://lifehacker.com/software/ubuntu/ubuntu-tip--how-to-mount-a-windows-ntfs-partition-203102.php)

---

### Post by kuhlbeans on 2008-12-13
I have the following in my fstab:

```

/dev/sda1 /media/windows ntfs rw,user,exec 0 0

```

One thing that may be causing you a problem is you're trying to mount as Windows Drive with a space in it.  I'm not sure how fstab handles spaces, you may need to escape with \ or surround the location in quotes, as in "\media\Windows Drive".  Alternatively, you could use a name without a space (e.g. just windows like I do).

---

### Post by TeXtonyx on 2008-12-13
> **kuhlbeans said:**
> I have the following in my fstab:

```

/dev/sda1 /media/windows ntfs rw,user,exec 0 0

```

One thing that may be causing you a problem is you're trying to mount as Windows Drive with a space in it.  I'm not sure how fstab handles spaces, you may need to escape with \ or surround the location in quotes, as in "\media\Windows Drive".  Alternatively, you could use a name without a space (e.g. just windows like I do).

This is my fstab:
/dev/sda1 /media/WindowsPro ntfs-3g defaults,locale=en_US.UTF-8 0 0

I also have no space, I don't know that it matters, but be safe
and make a directory with just one word, /mnt/oneword

First, do sudo fdisk -l
which will list your Windows partition for sure, use that report.

sudo mount -t ntfs /dev/sdb1 /dev/Windows

Then, ls /dev/Windows and you should see your Windows partition.
If Windows was not dismounted cleanly, then you cannot mount it
until you shut down Windows cleanly. Or you can try to force
the mount of the Windows partition, but you should fix Windows.

The ntfs-3g driver is what lets you read/write to Windows.
I also ran ntfs-config to set up my /media/Windows fstab entry.

I think you should make a new directory say, /mnt/Windows<--
and edit fstab and delete the "Drive" from /mnt/Windows Drive

/dev/sda1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

or the entry below should work.

/dev/sda1 /media/windows ntfs rw,user,exec 0 0

Is your problem really that Windows won't boot? Actually I
think the problem is using the space to name the directory
of /Windows Drive, just use one word. Pay attention to
Capital letters, Windows does not equal windows

---

### Post by Audi0Fr3ak on 2008-12-13
New error, I managed to figure out the NTFS Configuration tool

```

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/Server_Drive -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/Server_Drive ntfs-3g force 0 0

```


EDIT: Forgot to mention I HAVE formatted the drive, so no windows partition exists, I don't understand what would be using it.

---

### Post by drs305 on 2008-12-13
If you don't have anything on the device, you can install ntfsprogs and then run ntfsfix to possibly clear the message. You actually can run ntfsfix on partitions with data on them, it's just safer to try to fix it via Windows in that case.

```

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1

```

---

### Post by Audi0Fr3ak on 2008-12-14
But i DO have stuff i want off there... So that wouldn't work, if it was empty id just reformat it to FAT32...

---

### Post by drs305 on 2008-12-14
> **Audi0Fr3ak said:**
> But i DO have stuff i want off there... So that wouldn't work, if it was empty id just reformat it to FAT32...

Well, actually, it probably *would* work. It's just safer to do it through windows. You can read about ntfsfix by typing "man ntfsfix" in a terminal. If you get to the point where you have no other ideas, if it were my disk I would run it without reservation. I have used it on several occasions without any problems but remember that ntfs is not a native linux file system and is trying its best to deal with it.

---

### Post by Audi0Fr3ak on 2008-12-14
I managed to get it..

I restarted, and when i tried getting in, it told me i didn't have sufficient privileges. I typed gksudo nautilus

and im in!

thanks to all

---

