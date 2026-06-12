---
title: "Some backup questions"
date: 2009-02-28
forum: General Help
---

### Post by sofasurfer on 2009-02-28
1) If you want to restore your system, which is what a backup is all about, why is there an option for preserving permissions (-p). Isn't preserving permissions an OBVIOUS requirement for a backup?

2) Aren't hardlinks the same as windows shortcuts? Why all the specifications required for dealing with hardlinks? Again, if you want to restore your system don't you OBVIOUSLY want ALL things to be duplicated?

3) Don't a lot of you think that all the websites that deal with TAR backups should be deleted and started over? The majority of them are years old and seem to be a little obsolete. How old of a TAR script can you still count on being functional, in regards to newer/updated options and such?

I have noticed that there are thousands of differant backup scripts on the web. They say that it is because ever person has differant needs. But there are not THAT many needs. I think that most scripts are simply an attempt to create ones own version based on another persons version. But the end result is many scripts that do the same thing but are written differantly and this just multiplies the confusion ten-fold.

I'll stop writing now because I am getting to urge to go off into a rant because of my frustration.

---

### Post by albinootje on 2009-02-28
> **sofasurfer said:**
> 1) If you want to restore your system, which is what a backup is all about, why is there an option for preserving permissions (-p). Isn't preserving permissions an OBVIOUS requirement for a backup?

If you're in a hurry to copy all files from a full 1000 Gb disk, then it is a lot faster to copy your data without preserving permissions and time stamps.
> 
2) Aren't hardlinks the same as windows shortcuts?

I think MS-Windows shortcuts are comparable with symbolic links in Linux. 
Hard links in Linux are -real- files, not just a referral.
(see : man ln)

---

### Post by amauk on 2009-02-28
> **sofasurfer said:**
> 1) If you want to restore your system, which is what a backup is all about, why is there an option for preserving permissions (-p). Isn't preserving permissions an OBVIOUS requirement for a backup?Yes, it's an obvious requirement of backups to preserve ownership & permissions
but tarballs are not used purely for system backups

If Bob creates a tarball, preserving ownership and permissions, and sends it to Bill
Bill will have a problem accessing the files, as they're owned by Bob (or a non-existent user)

Usually you do not want to preserve ownership or permissions
but with system backups, you do - hence the options

> **sofasurfer said:**
> 2) Aren't hardlinks the same as windows shortcuts? Why all the specifications required for dealing with hardlinks? Again, if you want to restore your system don't you OBVIOUSLY want ALL things to be duplicated?
No, hardlinks are not the same
the closest thing Windows has to hard links is the mount junctions on newer NT systems

A windows shortcut is equivilent to a Unix symlink (aka soft link)

Soft links link to files on the filesystem level
Hard links link to block addresses on a device level

the standard '.' & '..' directories for current & parent dir are examples of hard links

> **sofasurfer said:**
> 3) Don't a lot of you think that all the websites that deal with TAR backups should be deleted and started over? The majority of them are years old and seem to be a little obsolete. How old of a TAR script can you still count on being functional, in regards to newer/updated options and such?

I have noticed that there are thousands of differant backup scripts on the web. They say that it is because ever person has differant needs. But there are not THAT many needs. I think that most scripts are simply an attempt to create ones own version based on another persons version. But the end result is many scripts that do the same thing but are written differantly and this just multiplies the confusion ten-fold.

I'll stop writing now because I am getting to urge to go off into a rant because of my frustration.
people tend to write custom scripts to suit there own needs
what can I say
you can't just "delete" a webpage cause it's old - the net doesn't work like that

You may be better off with a specific backup program, like rsync-backup
they automate a lot of the donkey work involved in creating and restoring backups

---

### Post by sofasurfer on 2009-03-10
This question pertains to the snapshot file (.snar) that is created in the tar 'listed-incremental' process.

Say I create a full backup with the following command...
```

sudo tar cpvf backup.1.tar --listed-incremental=/home/backup.snar /home/user/Pictures 

```

I would end up with a tar achive named  backup.1.tar and a snapshot named backup.snar.

Now, I want to add my /Desktop directory to the archive by running...

```

sudo tar -cpvf backup.2.tar --listed-incremental=/home/backup.snar /home/daryl/Desktop

```

Does this add data to the pre-existing .snar file or does it replace the .snar file altogether?

The GNU Tar manual states...
```

Some time later you create another incremental backup. You will then see: 	
$ tar --create \
           --file=archive.2.tar \
           --listed-incremental=/var/log/usr.snar \
           /usr
tar: usr/local/db: Directory is new
usr/local/db/
usr/local/db/data
usr/local/db/index

The created archive &#8216;archive.2.tar&#8217; will contain only these three members. This archive is called a level 1 backup. Notice that &#8216;/var/log/usr.snar&#8217; will be updated with the new data, so if you plan to create more &#8216;level 1&#8217; backups, it is necessary to create a working copy of the snapshot file before running tar. The above example will then be modified as follows:
 	

$ cp /var/log/usr.snar /var/log/usr.snar-1
$ tar --create \
           --file=archive.2.tar \
           --listed-incremental=/var/log/usr.snar-1 \
           /usr



```

I don't understand this. The command as shown, first shows just the level 1 'tar' command and then it later shows that I must first copy the level 0 snar file to .snar-1 before I run the level 1 command.

If this is the case, then for every level 1 archive (archive.2.tar, archive.3.tar, archive.4.tar, etc) I create, do I need to create more .snar files (.snar-2, .snar.3, .snar.4, etc)?

I guess another way of asking this is, does every dump (full and incremental) have its own snapshot file?

Thats enough for now. I hope I made myself clear.

---

### Post by sofasurfer on 2009-03-11
bump

---

