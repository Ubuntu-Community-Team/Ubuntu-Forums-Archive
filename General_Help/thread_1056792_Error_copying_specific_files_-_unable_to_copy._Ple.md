---
title: "Error copying specific files - unable to copy. Please help!"
date: 2009-02-01
forum: General Help
---

### Post by Pipps on 2009-02-01
I am receiving an error message when attempting to copy files and I am unable to perform the copy. 

The problem occurs when running Ubuntu normally and also when attempting to perform the operation using the live CD.

The files which I am attempting to copy are the files which comprise one of the several directories of my Ubuntu installation.

By way of background, my Ubuntu installation is partitioned as follows:

sda1 - /boot (ext3)
sda6 - / (ext3)
sda7 - swap (n/a)
sda8 - /usr (ext3)
sda9 - /var (ext3)
sda10 - /home (ext3)

When I load Ubuntu using the Live disc, and I attempt to copy and paste the contents of a drive, say 'sda6', I receive the following error message as soon as I have clicked 'paste':
> 'Error while copying: Can't open mountable drive.'

When I attempt to try this copy and paste operating in the terminal when in Live mode, I use the following command:
> "cp /media/disk-2 /media/IOMEGA_HDD/LinuxBackup[Home]"
However, I receive the following response from the terminal prompt:
> "cp: omitting directory '/media/disk-2'."

Why am I unable to copy and paste the contents of my installation drives to a removable disc?

Please help!

---

### Post by dexter on 2009-02-01
For your second issue, you need to copy your files recursively:
```
cp -R sourceFolder DestinationFolder 
```

---

### Post by Pipps on 2009-02-01
That is wonderful - thank you!

May I also ask: How would I do this whilst using the tar function for the target article at the same time?

---

### Post by geirha on 2009-02-01
To create an archive of the contents of /media/disk-2, you can do the following:
```

# archive with no compression
cd /media/disk-2/ ; sudo tar cf "/media/IOMEGA_HDD/LinuxBackup[Home]/backup.tar" .
# with gzip-compression:
cd /media/disk-2/ ; sudo tar zcf "/media/IOMEGA_HDD/LinuxBackup[Home]/backup.tar.gz" .
# with bzip2-compression:
cd /media/disk-2/ ; sudo tar jcf "/media/IOMEGA_HDD/LinuxBackup[Home]/backup.tar.bz2" .

```
Don't forget the . at the end of each tar command.

---

### Post by Pipps on 2009-02-01
Thank you! :)

And will either of those commands overcome the recursive problem too?

---

### Post by Pipps on 2009-02-01
Will the following command work for a recursive copy?

```
cd /media/disk-2/ ; sudo tar zcf "/media/IOMEGA_HDD/LinuxBackup[Home]/backup.tar.gz" .
```]

Thank you! :)

---

### Post by geirha on 2009-02-01
> **Pipps said:**
> Will the following command work for a recursive copy?

```
cd /media/disk-2/ ; sudo tar zcf "/media/IOMEGA_HDD/LinuxBackup[Home]/backup.tar.gz" .
```]

Thank you! :)

That tar-command will archive everything under /media/disk-2/ recursively, yes.

---

### Post by Pipps on 2009-02-01
Thank you! :D

---

### Post by Pipps on 2009-02-03
May I ask one further question which may prove to be important?

When I come to wanting to paste all of the previously copied files back into their respective partitions on my local hard drive, whilst in Live CD mode, so as to constitute a fully working operating system again, will I be likely to experience any problems in doing so, or should the paste operate complete in a straightforward manner?

---

### Post by geirha on 2009-02-03
If by pasting you mean extracting ("untaring") the archive, then there shouldn't be much of a problem. When archiving something with tar, as root (in this case with sudo), the default behavior is to store the files' ownership, permissions and timestamps along with the files. So when you extract it, it should be identical in every way; with one catch:

The ownership is not stored by usernames, but by uid (user id). When you create users, the first user typically gets uid 1000, and the next user gets 1001, then 1002 and so forth. So if you reinstall for some reason, and create the same users you had earlier, but in a different order, then the ownership of the archived files may have different ownerships when you extract them. You can see which uid each user has by looking in the file /etc/passwd. For a description of the passwd file's format, run ```
man 5 passwd
```

The command to e**x**tract is very similar to **c**reating the archive.
```
cd /media/disk-2/ ; sudo tar zxf "/media/IOMEGA_HDD/LinuxBackup[Home]/backup.tar.gz"
```

---

### Post by Pipps on 2009-02-04
That is absolutely brilliant advice!

Thank you! :)

---

