---
title: "Rsync From Ubuntu to NTFS"
date: 2009-01-11
forum: General Help
---

### Post by Buce on 2009-01-11
I'm trying to rsync from my ubuntu laptop to an ntfs drive mounted on a desktop that is also running ubuntu. The command I'm using is: ```
sudo rsync -av --delete --exclude-from "/home/<user>/.rsync/exclude" /home/ <user>@<host>:/symlink/to/ntfs/drive
```
The ~/.rsync/exclude file contains: ```
*cache*
*Cache*
*CACHE*
.thumbnails
*.thumbnails* #not sure if line above will do what i want it to
```
Since I have a lot of data to transfer, I haven't run the command to completion yet, but I'm noticing a lot of 'failed to set times on "/path/to/directory": Operation not permitted' errors. When I look at the directories referred to by these errors, it looks some or all of the files aren't being transferred.

What is the cause of this? Does it have something to do with rsyncing from ext3 to ntfs? If so, is there a workaround I can use to ensure that every file in my home directory is copied to the backup drive? If someone could provide a solution, or point me to a link with some relevant info, I'd be very appreciative.

---

### Post by mdurham on 2009-01-11
I use "sudo rsync -rltx ..." to sync to FAT32 so I guess it will be okay for NTFS. I think that you will loose file permission stuff though if going from ext3.

---

### Post by bryncoles on 2009-01-11
i know rsync has trouble running if the file system your moving to  is fragmented - often causes it to error out. do you have windows handy? can you defrag the ntfs partition and then try running rsync again? this is why i dont have my external drives in NTFS or FAT, as i no longer have windows around...

---

### Post by bryanl on 2009-01-11
> a lot of 'failed to set times on "/path/to/directory": Operation not permitted' errors.
I get that with CIFS shares mounted with the nounix option.

---

### Post by Buce on 2009-01-11
Thanks for the responses. I'll try defragging and using the options mdurham suggested, and then let you know the results.

---

### Post by Buce on 2009-01-11
I'm still getting the same errors, but it after a cursory look, it seems like the files are getting transferred anyway. Guess I'll just cross my fingers, hope it works, and check the total size of the top-level directory's contents when it's finished.

---

### Post by ameno on 2009-02-22
i wrote some backup scripts and want to save some of my files to an external ntfs volume and have the same problem as you atm.

im not sure yet, but i think the problem is:
the -a option implies -p, which means preserve permissions.
ntfs-3g mounts the whole volume with a fixed umask, even root cant change file permissions.
but you tested without -p... so maybe im wrong

---

### Post by Buce on 2009-03-14
Sorry for the late reply. I'm still a newb here, and I have this nasty habit of not posting for a while, for fear I might claim something works only to have it break a bit down the line.

I think getting rid of the -a flag worked. IIRC, I still got error messages, but the data all seemed to be fine. It's been a while since I've done a backup, though, and I can't test it cause my backup computer won't boot to Ubuntu for some reason... :(

Anywho, the final command I used was:
> sudo rsync -rhltxyz --modify-window=1 --progress --stats --ignore-errors --delete-after --delete-excluded --exclude-from /home/user/.rsync/exclude /home/user [email]user@host:./etc/user.backup[/email]
There's a lot of frivilous options in that command, but a look through the man pages should help to sort out what's essential and what isn't.

---

### Post by hyper_ch on 2009-03-14
remember, ntfs won't support file permissions and ownership. I'd really not rsync onto ntfs.

---

