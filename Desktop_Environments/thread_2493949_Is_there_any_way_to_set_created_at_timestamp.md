---
title: "Is there any way to set created at timestamp?"
date: 2023-12-30
forum: Desktop Environments
---

### Post by norvel4 on 2023-12-30
So I have a file properties recorder that records to system precision but is there any way to set all and I do mean all timestamps including changed at and created at programmatically? Like could I somehow like make a backup file like I already can then set all timestamps like before restore happened? Can it be with files already there because I would prefer to be able to use rsync mostly for transfer? If not can someone at Ubuntu make a future release allow it?

---

### Post by TheFu on 2023-12-31
No. BTW, nobody here works for Canonical and a single post isn't sufficient to get the 3+ months of expert developer effort per file system to happen.  

You can use rsync with sudo to maintain most, but not all, timestamps.  There are OS and file system dependencies involved. Not all file systems support touching the "birth timestamp", so there's no way to modify it for higher level tools, like rsync.

Most proper backup tools will maintain timestamps that are necessary for their needs, along with owner, group, ACLs, xattrs, which are absolutely MORE critical to backup-restore processing than the birth time for a file.

If you would like to waste a bunch of storage, you can backup at the file system or entire partition level, but that is a fools effort for many reasons.  Basically, you'd be backing up at the device level, which breaks backup versioning.

Canonical is the company that packages Ubuntu.  About 99% of the OS is feed by other project teams/companies from outside Canonical. They only create software for a tiny portion of the OS - mainly related to GUI add-ons, installation, and a few server-specific tools like netplan, lxd, snap and the glue scripts that make those things work together in the GUI.  

They don't do file system internals to my knowledge on a regular basis, so if you want a file system to be changed for some specific reason - and it will need to be a very good reason beyond "it isn't right", then you'll need to open a bug with the specific file system development team, make your case, wait for it to be implemented, then work on each project higher in the software stack to support those modifications - cp, mv, rsync (really librsync), backup tools, would each need to be modified.  And if you use other layers, like network access to storage, those tools would need to be modified as well.

Of course, if you provide the necessary patches to the file system team to implement what you seek and if that code is very clean, doesn't break anything else in the form of a regression, and gets accepted, it will really speed up your cause.  But there's always another file system, so you'll need to do this for ext4, xfs, zfs, btrfs, just to make changing cp, mv, rsync, nfs, samba, worth the effort. That's my guess in the 5 minutes I've spent thinking about this effort.

Or did I completely misunderstand the question/issue?

---

### Post by norvel4 on 2023-12-31
> **TheFu said:**
> No. BTW, nobody here works for Canonical and a single post isn't sufficient to get the 3+ months of expert developer effort per file system to happen.  

You can use rsync with sudo to maintain most, but not all, timestamps.  There are OS and file system dependencies involved. Not all file systems support touching the "birth timestamp", so there's no way to modify it for higher level tools, like rsync.

Most proper backup tools will maintain timestamps that are necessary for their needs, along with owner, group, ACLs, xattrs, which are absolutely MORE critical to backup-restore processing than the birth time for a file.

If you would like to waste a bunch of storage, you can backup at the file system or entire partition level, but that is a fools effort for many reasons.  Basically, you'd be backing up at the device level, which breaks backup versioning.

Canonical is the company that packages Ubuntu.  About 99% of the OS is feed by other project teams/companies from outside Canonical. They only create software for a tiny portion of the OS - mainly related to GUI add-ons, installation, and a few server-specific tools like netplan, lxd, snap and the glue scripts that make those things work together in the GUI.  

They don't do file system internals to my knowledge on a regular basis, so if you want a file system to be changed for some specific reason - and it will need to be a very good reason beyond "it isn't right", then you'll need to open a bug with the specific file system development team, make your case, wait for it to be implemented, then work on each project higher in the software stack to support those modifications - cp, mv, rsync (really librsync), backup tools, would each need to be modified.  And if you use other layers, like network access to storage, those tools would need to be modified as well.

Of course, if you provide the necessary patches to the file system team to implement what you seek and if that code is very clean, doesn't break anything else in the form of a regression, and gets accepted, it will really speed up your cause.  But there's always another file system, so you'll need to do this for ext4, xfs, zfs, btrfs, just to make changing cp, mv, rsync, nfs, samba, worth the effort. That's my guess in the 5 minutes I've spent thinking about this effort.

Or did I completely misunderstand the question/issue?

I just wanted a way to back up and restore all on a file system and rsync does not do that. I understand "important" stuff is backed up but I prefer everything. I already have a property recorder program. I understand no one here is with Canonical but if anyone has a solution and I do not need Canonical I would prefer to know. I already contacted Canonical. I do not need tools to be able to do created at themselves mostly but one way to set created at would be good. You seem to understand. Anyway, if you know who I should contact plesase let me know. All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

---

### Post by TheFu on 2023-12-31
> **norvel4 said:**
> I just wanted a way to back up and restore all on a file system and rsync does not do that.

rsync isn't designed to backup file systems.  If you want that, you'll need to go to the device level.  There are a few tools for this, but in general, it is foolish to do backups that way.  For a 1-time clone, an argument could be made that backing up the entire filesystem is 1 method.  I used to do that, then I had my eyes opened and clearly saw the waste that caused and learned why it wasn't necessary for an excellent backup and restore process.

YMMV.

> **norvel4 said:**
> 
 I understand "important" stuff is backed up but I prefer everything. 

Nothing is backed up, unless you do it yourself. There's no magic "backup" button anywhere. If you didn't do it, it isn't happening.

IMHO, you'd be better off learning to use one of the excellent backup tools, like duplicity or rdiff-backup.  If you want better backups, use ZFS or LVM and learn to use snapshots that can be pulled remotely.

Trying to solve a problem that doesn't actually exist is less useful if you want to be practical.  If you are trying to meet some legal requirement, then buy lots of storage, expect to waste lots of time, to achieve what you seek with **fsarchive** or **dd** or **ddrescue**.  These are NOT industry standard methods, however.

I've said what I needed to say. Use it or ignore it. Completely up to you.

---

### Post by norvel4 on 2023-12-31
Thanks, I was trying for a full backup that could easily be used on any computer. I found Java may have a specific thing for setting created at and changed at. I think I know what I am doing and it seems rsync was not made for this but it can do it. Also, like my Disks tries to back up all space including empty space and like my system is 2TB so that is impractical. I have a slow 2.1TB USB but would prefer to have only filled space copied. All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

---

### Post by norvel4 on 2023-12-31
I tested Java and it failed so no way to set created at timestamps. All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

---

### Post by TheFu on 2023-12-31
> **norvel4 said:**
>  All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

that statement isn't translating in any useful way.  May as well say "yada, yada, yada, yada, yada, yada, yada, yada, yada, yada"

---

### Post by norvel4 on 2023-12-31
Well congratulations me, I found debugfs can do this job and be executed by Bash maybe or maybe not, maybe.

---

### Post by The Cog on 2023-12-31
Oh well played, Sir.

---

### Post by norvel4 on 2023-12-31
I did find "debugfs" is a development thing and supposedly not fit for "regular" use but it is only way to do this that I have found and it allows setting like all file properties. It is an all Linux thing and debugfs can be used on Linux formatted USBs. Maybe code from me soon, maybe I will open source. This is a step towards better backups for me. Easy enough to use on Windows although I would have to install a thing for ext4 reading. This method should also be able to be used on almost any Linux and maybe some Unix. Anyway, problem solved. Thank you for trying to help. All as per one might be maybe or might not be maybe, maybe or maybe not, maybe.

---

