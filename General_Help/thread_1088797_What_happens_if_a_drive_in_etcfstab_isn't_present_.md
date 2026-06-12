---
title: "What happens if a drive in /etc/fstab isn't present when the system boots?"
date: 2009-03-06
forum: General Help
---

### Post by Roasted on 2009-03-06
I have 4 drives in my computer. All mounted via fstab upon boot.

I was just thinking, if one of those drives failed (without the OS on it) what would happen when I boot up? Would Ubuntu just bypass the non-responsive channel that the drive was plugged in and mount the other 3?

I originally did my install with only 1 drive plugged in to keep things simple. Then I added the other 3 and added them to fstab. Would it be expected to have any GRUB errors if one of the drives is missing from fstab as I boot?

---

### Post by azzamite on 2009-03-06
If your drive isn't in fstab, it is ignored, no real harm on that.
If your drive is USB, you'll be able to mount it as any other USB drive.

If you remove any drive/partition that is mounted on boot via fstab,
your system won't boot, and you'll enter to the recovery console (that's
happend to me some times).

You won't get grub error unless you try to boot from a non existent
drive/partition.

---

### Post by HermanAB on 2009-03-06
Nothing much - it just won't get mounted - unless the missing drive has something important on it needed to boot the system.  It can be a bother, but a "mount -a" on the command line can fix things later.

Cheers,

Herman

---

### Post by Seq on 2009-03-06
If you are using UUIDs to mount your partitions in fstab, only the missing partition will not show up. If you were using identifiers like /dev/sdXY your drives may re-order (depending on type of failure).

As a simple example: If your drive labelled 'sdb" fails/is not detected/is removed, on your next boot you will still have a sdb, but it will likely be the drive formerly identified as sdc. So your /var could end up at /home, for example. This is a problem UUIDs solve.

---

### Post by Roasted on 2009-03-06
I have them mounting by UUID.

A drive = OS/Home Dir
B drive = Backup of Home Dir
C drive = Where Samba users back up to
C drive = Backup of drive C

I only need drive A to boot. But if I boot up and C isn't detected, then what? Does Ubuntu crap its pants and not boot?

Last week I had it come up saying something failed. I thought a drive failed. I rebooted and it was perfectly fine. I was so confused. I wasn't sure if my system would hang and be un-bootable if drive B, C, or D failed.

---

### Post by Seq on 2009-03-06
> **Roasted said:**
> I have them mounting by UUID.

A drive = OS/Home Dir
B drive = Backup of Home Dir
C drive = Where Samba users back up to
C drive = Backup of drive C

I only need drive A to boot. But if I boot up and C isn't detected, then what? Does Ubuntu crap its pants and not boot?

If a drive fails, all other drives will still be mounted (because you are using UUIDs, there will be no surprises or mis-mounts).

The only time I see delays on my machines when a mount is unavailable is for nfs mounts in fstab (has to wait for a timeout). So you shouldn't have a problem booting.

> **Roasted said:**
> Last week I had it come up saying something failed. I thought a drive failed. I rebooted and it was perfectly fine. I was so confused. I wasn't sure if my system would hang and be un-bootable if drive B, C, or D failed.

Without seeing what the error was...

---

### Post by Roasted on 2009-03-07
Okay, if a drive goes down I can still boot. I got that.

But what would crontab do if it comes that time of the day to do a backup and my backup drive is down? Does crontab simply not run? Would I get any errors or any notifications about anything of any sort?

---

### Post by HavocXphere on 2009-03-07
Not sure what gnome does, but the dolphin file manager puts a note at the bottom that it can't mount it.

The cron thing would depend on the backup program in use. It will probably write something into its own log file.

---

### Post by Roasted on 2009-03-07
Hmm, but my point is, I won't get bombarded with a buttload of errors and stuff, would I? 

If it can't mount it and it simply tacks into a log file "was unable to mount monday morning @ 3:30 am" then that's fine. But if my system self destructs because crontab couldn't find my 3rd drive to run my backup script, then we have a problem.

---

### Post by Seq on 2009-03-07
> **Roasted said:**
> Okay, if a drive goes down I can still boot. I got that.

But what would crontab do if it comes that time of the day to do a backup and my backup drive is down? Does crontab simply not run? Would I get any errors or any notifications about anything of any sort?

It depends. If you mount something on /backup (as an example) and your cron copies stuff to /backup, it will still work -- it will just back up to your root drive. This is probably not what you want. If your cron job copies stuff to /backup/someotherfolderthatdoesnotexist, then it will possibly fail, depending on the behaviour of whatever you are running from cron.

If your backup program that gets run is actually on the missing drive, you'll get an error in your log whenever cron tries to run it.

---

### Post by Roasted on 2009-03-07
I'm not sure I completely follow why my stuff would get backed up on root...

I have 4 drives, which have 5 partitions.

A - Root/Home
B - Localbackup
C - Storage
D - Storagebackup

If drive D fails, yet my rsync script is commanding the system to rsync C's contents to D, why would it use Root as a backburner to kick the data over to? I don't see why D's absence would put Root (only a 20gb partition) to pick up 170+gb of data from C...

---

### Post by Chris Musampa on 2009-03-07
Because if the drive/partition which was supposed to mounted at /mountpoint fails to mount then /mountpoint will be treated as a plain old directory.

---

### Post by Seq on 2009-03-07
> **Roasted said:**
> I'm not sure I completely follow why my stuff would get backed up on root...

I have 4 drives, which have 5 partitions.

A - Root/Home
B - Localbackup
C - Storage
D - Storagebackup

If drive D fails, yet my rsync script is commanding the system to rsync C's contents to D, why would it use Root as a backburner to kick the data over to? I don't see why D's absence would put Root (only a 20gb partition) to pick up 170+gb of data from C...

Exactly as Chris Musampa said. The file system is a single hierarchy, not multiple distinct hierarchies as you would have in Microsoft operating systems. As a simple example, lets pretend you have the following directories:

[LIST]
[*]/
[LIST]
[*]/backup
[LIST]
[*]/backup/computer1
[*]/backup/computer2
[/LIST]
[*]/home
[*]/var
[*]/etc
[/LIST]
[/LIST]

/backup is a separate partition mounted into the hierarchy. /home, /etc and /var are just part your root partition. The directories /backup/computer1 and /backup/computer2 are on your backup partition.

If you run the following two commands with /backup mounted, it will create those files.
```
touch /backup/file
touch /backup/computer1/file
```

Now, your scenario you were concerned was the drive containing the partition you are mounting at /backup failing. The physical directory /backup still exists, but obviously does not contain any data (that drive that usually mounts there is dead). Running the first 'touch' command above will work. /backup/file is created on the root partition. The second command would fail because the computer1 directory does not exist.

So if your backup script is simply creating a tar.gz in /backup, it will still work (and likely fill your root partition if it is small). If it is putting it /backup/computer1 instead, it MAY work. It depends on if your software creates missing directories.

For your use-case, this may seem like a bug because you don't want to fill your root partition. This is an unfortunate side-effect of the powerful hierarchy that Unix-like operating systems have. You can decide to move /var to an nfs share. Other than having to copy files to it, the system does not care if it is mounted over nfs, part of root, or it's own partition.

You may wish to check to see if your partition is mounted before you actually perform your backup. There is probably a better way, but off the top of my head: mount | grep " /backup " | wc -l

---

### Post by dcstar on 2009-03-07
> **Chris Musampa said:**
> Because if the drive/partition which was supposed to mounted at /mountpoint fails to mount then /mountpoint will be treated as a plain old directory.

And you run the risk of maxing out the filesystem that the mountpoint directory is on if you happen to do things like put (big, fat) backups on it.....   :-(

All sorts of unwanted consequences can occur if your mounted drives don't mount....

---

### Post by dcstar on 2009-03-07
> **Seq said:**
> 
.........
You may wish to check to see if your partition is mounted before you actually perform your backup. There is probably a better way, but off the top of my head: mount | grep " /backup " | wc -l

Or have the fstab entry set to not auto-mount, and then just use the mount command at the start of the backup script with a fail if it doesn't.

---

### Post by Roasted on 2009-03-07
Not gonna lie here, I've used Ubuntu for the last 4 years, and up until now I've been surprised at the great way they handle the OS.

But I have to admit here, this is laughable to hear that Linux would simply write files to another directory when one fails.

I understand what you guys are saying, but why in the world would Linux decide, oh! It wants me to write data here on drive C! But! Drive C is not there! So let's just toss it over here on the root partition that is 1/200th the side of the data to be moved!

I guess it's just flawed logic in my mind that if a mount point fails that any activity that would otherwise go to that mount point would fail too. It's a poor keepsafe to fill in the blank with the missing drive, in my opinion.

---

### Post by Seq on 2009-03-07
> **dcstar said:**
> Or have the fstab entry set to not auto-mount, and then just use the mount command at the start of the backup script with a fail if it doesn't.

This is better anyway. If your machine has any problems, your backup filesystem is not mounted at all.

---

### Post by Seq on 2009-03-07
> **Roasted said:**
> Not gonna lie here, I've used Ubuntu for the last 4 years, and up until now I've been surprised at the great way they handle the OS.

But I have to admit here, this is laughable to hear that Linux would simply write files to another directory when one fails.

I understand what you guys are saying, but why in the world would Linux decide, oh! It wants me to write data here on drive C! But! Drive C is not there! So let's just toss it over here on the root partition that is 1/200th the side of the data to be moved!

I guess it's just flawed logic in my mind that if a mount point fails that any activity that would otherwise go to that mount point would fail too. It's a poor keepsafe to fill in the blank with the missing drive, in my opinion.

The issue is that you didn't say "Put the backups on Drive C", you said "Put the backups in /backup". Why would cp or tar care where or what that filesystem is?

You have /. You can optionally move any directory you want to other file systems or access via other means. The whole point is that it is transparent and programs do not care.

I suppose you could get into doing things like making /backup (unmounted) have no permissions. These should be overridden by the mounted partition. The following code should make /backup inaccessible if the corresponding mount is not present. I just tried it with an nfs4 mount and it worked for me, but test it before you rely on it.

```
sudo umount /backup
sudo chmod 000 /backup
ls -l / | grep backup
sudo mount /backup
ls -l | grep backup
```

---

### Post by Roasted on 2009-03-07
What issue didn't I say? My issue is very clean cut and clear.

By UUID, I have my drives mounting automatically in fstab to specific directories.

Drive B, for example, gets mounted to /media/localbackup.

When I unplug Drive B and run my script, the script runs. It just goes. Why? It makes SENSE for it to fail if /media/localbackup is not present. /media/localbackup is reserved for Drive B. Drive B is not present. Yet, it still throws data around. Why? It makes no sense for the data to get kicked over to my root partition.

I just tested this and now I have 6 gig that got kicked onto my root partition that I cannot find to delete to free up.

Not gonna lie, I expected better from Ubuntu.

EDIT - Let's put it this way. I'll share with you guys what I need and maybe you guys have a better idea of something that'll work better for me.

I'm running Ubuntu 8.10 64 bit. I have Samba running. I have 4 drives in my computer. Two are mine (1 drive is a backup) and two are network drives (1 for samba users to backup to and the last drive to make a copy). So I have some decent redundancy going on considering it's a home network.

What I need is the ability to have backups ran automatically. If the drive fails, the process fails. Period. Done. If running crontab+rsync on my backup system here is going to threaten the stability of Ubuntu in the sense of a drive failing yields a guarantee for my root partition to be maxed, then I'm sorry, but Ubuntu is not the best choice for backups to be ran to and I will use my Vista machine to handle this task.

Oh, and PS - How do I find where the data was stored on the root partition so I can recover my other 6 gig from it?

---

### Post by dcstar on 2009-03-07
> **Roasted said:**
> What issue didn't I say? My issue is very clean cut and clear.

By UUID, I have my drives mounting automatically in fstab to specific directories.

Drive B, for example, gets mounted to /media/localbackup.

When I unplug Drive B and run my script, the script runs. It just goes. Why? It makes SENSE for it to fail if /media/localbackup is not present. /media/localbackup is reserved for Drive B. Drive B is not present. Yet, it still throws data around. Why? It makes no sense for the data to get kicked over to my root partition.
.......

Firstly, you should **not** put removable drives in fstab, it is not intended for any removable media - that is exactly why the /media folder exists and entries are only created in there when the media exists.

The problem you have is because you have misconfigured your system.

If you want a system that works, remove the fstab entries and label all the removable partitions then they will always be mounted in /media using those names, if they are not plugged in then they will not be there.

---

### Post by Seq on 2009-03-07
> **Roasted said:**
> Drive B, for example, gets mounted to /media/localbackup.

When I unplug Drive B and run my script, the script runs. It just goes. Why? It makes SENSE for it to fail if /media/localbackup is not present. /media/localbackup is reserved for Drive B. Drive B is not present. Yet, it still throws data around. Why? It makes no sense for the data to get kicked over to my root partition.

[snip]

What I need is the ability to have backups ran automatically. If the drive fails, the process fails. Period. Done. If running crontab+rsync on my backup system here is going to threaten the stability of Ubuntu in the sense of a drive failing yields a guarantee for my root partition to be maxed, then I'm sorry, but Ubuntu is not the best choice for backups to be ran to and I will use my Vista machine to handle this task.

See my previous post regarding permissions. This will probably give you the behaviour you are after.

Note this is not an Ubuntu thing, but a unix thing. Solaris, FreeBSD and Mac OS X will all behave the same way. Windows does not (by default) because different partitions get placed in different drive prefixes. You can't easily say "C: is getting full. I'm going to move "C:/Documents and Settings" to "D:/Documents and Settings" without having to change a bunch of ENV vars and registry settings and hope the programs you use read them.

At least as of XP, you can actually take a partition and place it within another drive's hierarchy. So you COULD actually have "C:/Documents and Settings" on it's own partition. But you'd have the exact same issue we are discussing here if that drive failed.

The reason it doesn't fail by default is because the operating system should not guess or assume what you want it to do. Guessing is undefined behaviour, which is very, very bad.

> **Roasted said:**
> I just tested this and now I have 6 gig that got kicked onto my root partition that I cannot find to delete to free up.

[snip]

Oh, and PS - How do I find where the data was stored on the root partition so I can recover my other 6 gig from it?

You can't see them because you mounted something over it. umount the directory and you can rm the files.

---

### Post by Seq on 2009-03-07
> **dcstar said:**
> Firstly, you should **not** put removable drives in fstab, it is not intended for any removable media - that is exactly why the /media folder exists and entries are only created in there when the media exists.

The problem you have is because you have misconfigured your system.

If you want a system that works, remove the fstab entries and label all the removable partitions then they will always be mounted in /media using those names, if they are not plugged in then they will not be there.

This assumes he is running a graphical system and logged in. And (from what I've been reading) his drives are not removable.

---

### Post by Roasted on 2009-03-08
My drives are not removable. I have four SATA drives that are plugged into my system that stay there.

My concern is, again, if a drive FAILS. I'm concerned about the consequences of my backup setup when a drive fails. It honestly seems inevitable that if a drive fails, I will have a serious problem with my system... at which point I'd have to boot to a LiveCD, track down the data that resides on the root partition, and delete it.

But, again, where is this data on my root partition? I want to find it so I can free up the 6 gigs sitting on it.

Isn't there any genius way to run backups on an Ubuntu computer that won't ultimately end in a FUBAR'd system if a drive fails? I mean, again, if a drive fails, it fails, I have to deal with that. But I think it's laughable to know that my entire system may be FUBAR'd along with it. Isn't there any sort of backup system or program I can use in Ubuntu that's actually built with a bit of intelligence?

---

### Post by Seq on 2009-03-08
> **Roasted said:**
> But, again, where is this data on my root partition? I want to find it so I can free up the 6 gigs sitting on it.

Isn't there any genius way to run backups on an Ubuntu computer that won't ultimately end in a FUBAR'd system if a drive fails? I mean, again, if a drive fails, it fails, I have to deal with that. But I think it's laughable to know that my entire system may be FUBAR'd along with it. Isn't there any sort of backup system or program I can use in Ubuntu that's actually built with a bit of intelligence?

Did you read any of my last few posts?

Changing the permissions of the umounted folder will make that folder unwritable unless your drive is mounted. This is what you want.

You don't need to boot with a livecd to delete those files. umount your partition and you will see the files you want to delete. Delete them. mount your partition again.

EDIT: Feel free to contact me on Jabber or MSN and I'll walk you through finding your data. Contact details are in my profile (Jabber and MSN are the same address. Oddly enough, the forums do not have a jabber entry...)

---

### Post by Roasted on 2009-03-08
What kind of permissions are we talking?

For example, Drive C is my Samba network drive. I want my sambausers group to have "7" permissions to it so they can read/write/modify data in their share. I use "SyncToy" on the XP computers to synchronize the data to their share on my Ubuntu machine. So ultimately, I don't want anything to change on their end.

Are those the permissions you are talking about, 775 etc? The octal permissions?

Thanks for your help. I'll perhaps contact you later - got a football game to hit up right now. Thanks again!

EDIT - Okay, I understand what you guys are saying now. I wasn't getting the jist of it before. media/localbackup is just a folder, and when not mounted it's still sitting on the root directory. I got that now. So I can see why the data got pushed there. I unmounted my backup drive and sure enough, with it not mounted, the data was there that got accidentally copied before. I removed it and there was my root space back.

I'm just wondering, is there any way I can block read/write transmission to the backup folders UNLESS there's a mount point there?

---

### Post by Roasted on 2009-03-08
I went to the IRC chat with the Ubuntu channel and somebody took some time to explain this to me which actually works.

He said due to the fact I'm the only user on the system, I could get away with this, so I set it up like this. He said unmount the drives, then the existing mountpoints (ex - /media/localbackup) chown them to root:root, so therefore "jason" didn't have permission to write to that folder.

But once I mount my drives, I get the previous permissions back - jason:jason.

He also advised I take "sudo" out of my script and don't run the script as "sudo backup" but instead just "backup." 

Sure enough, it worked. In short, my backup setup is with ME only (jason) since I'm the only user. So since I'm copying my own home directory, which I have full reign of, to my backup drive, I can do so without the use of root.

Root has the ability to write anywhere.
Jason does not.
So if a drive would go down, I would get a permission denied error from running my script. I tested it and it does the job nicely.

So in short, my problem is solved. He said if I had 20 users, then this could be cumbersome when trying to rsync everybody's home directory... because THEN I'd have to use sudo/root, at which point I could try another command (something regarding the mount command) to check if the drive is mounted, and if it is, it would echo my rsync script.

Anyway, I'm good to go now. I appreciate everybody's help!

---

### Post by Seq on 2009-03-08
> **Roasted said:**
> What kind of permissions are we talking?

For example, Drive C is my Samba network drive. I want my sambausers group to have "7" permissions to it so they can read/write/modify data in their share. I use "SyncToy" on the XP computers to synchronize the data to their share on my Ubuntu machine. So ultimately, I don't want anything to change on their end.

Are those the permissions you are talking about, 775 etc? The octal permissions?

Thanks for your help. I'll perhaps contact you later - got a football game to hit up right now. Thanks again!

EDIT - Okay, I understand what you guys are saying now. I wasn't getting the jist of it before. media/localbackup is just a folder, and when not mounted it's still sitting on the root directory. I got that now. So I can see why the data got pushed there. I unmounted my backup drive and sure enough, with it not mounted, the data was there that got accidentally copied before. I removed it and there was my root space back.

I'm just wondering, is there any way I can block read/write transmission to the backup folders UNLESS there's a mount point there?

Yes. With it not mounted, remove all permissions (chmod 000 /media/localbackup). When you mount the drive in that place, the permissions should change back to what you normally want.

The code snip I posted a few posts ago should illustrate this. I used /backup as an example instead of /media/localbackup. I tested this with my /home folder mounted via nfs4 and it worked as expected -- when the nfs mount is missing, nothing can be written to that directory.

EDIT: Looks like you got it sorted out. Glad to hear.

---

### Post by Roasted on 2009-03-08
I have to wonder though, Seq... can you give me your thoughts on how I would accomplish this task but with multiple users?

Say I have 4 users on here. Well, Jason can access Jason... that's a given. But how can I access the other 3 home directories to be rsync'd? Well, without root, I can't.

Can you give me a "what you would do" synopsis of how you'd tackle that problem then? Basically, it's the same as I have it now, I need to avoid ANY chances of writing to the root partition assuming drive failure occures. But how would I kick over 4 home directories with the use of root while avoiding that chance?

---

