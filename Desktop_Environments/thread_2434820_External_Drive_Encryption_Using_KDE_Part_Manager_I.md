---
title: "External Drive Encryption Using KDE Part Manager In LXQT"
date: 2020-01-11
forum: Desktop Environments
---

### Post by springshades on 2020-01-11
Lubuntu version 19.10

The reason I'm posting to the desktop environment section is that I used KDE Partition Manager which is specific to the Qt side of things.

I've started an encryption job on a single partition 4 TB external 2.5 inch HDD drive connected via USB 3. I created a new partition table (GPT) and created a single partition encrypted using LUKS and formatted using ext3. The issue is that I'm now 12 hours into the job and the only feedback that I've seen from KDE Partition Manager is that the partition table was created successfully and the new partition format operation has started. The external HDD has an activity which is still flashing to show activity, so the drive appears to be doing *something*. This is being performed by a small box with an x5 8350 CPU which is not powerful but does support AES-NI. Currently, htop shows very little CPU activity however, so that doesn't seem to be the primary bottleneck.

I'm trying to figure out which one of the many possibility might be the case:

1. (Best case) These is something like a dd step being performed that just takes a while. Assuming this finishes in something like 24-48 hours I have no problem letting it continue to run.

2. The operation failed invisibly somewhere in the background. I need to stop the current operation and find some way to do it manually. Years ago, the frontends in both KDE and Gnome for partition management used to be absolute trash and failures like this used to happen ~50% of the time. For the last 5-10 years though, they've seemed much more reliable to me. I'm not sure how likely this scenario is.

3. My combination of hardware and options conflict in some way that I don't know about, and the software failed to warn me. Instead it decided to let me cause my own implosion because I was supposed to know that this was never going to work. (Probably the most Linux way of doing things).

4. (Worst case) I did everything right, but LUKS is somehow really, really slow for this type of operation, so this is going to take weeks and KDE Part Manager has no progress bar or feedback so I'll never know. Entirely possible. If that's the case, it would be nice to know now, so I can find some other way of doing it. I can use Veracrypt on another computer and then just move the pre-encrypted HDD over to this machine.

It's likely that the only response I'll get is ¯\_(&#12484;)_/¯ since it is so hard to know how long this takes for different combinations of hardware. It would be nice if anyone that has done encryption of several TB using LUKS could tell me whether this took you hours, days, or weeks to complete the operation though. It could help me narrow it down. Or maybe if there is a way that I can do this manually with a progress bar.

---

### Post by TheFu on 2020-01-11
Have you checked the system logs?  Anything in there about connection problems or low power on the USB port?

external 2.5inch HDDs without direct, external, power, only get power over USB.  That means it will be slow, very slow.
If you have a USB dock - they run $15-$25, you could pull the 2.5inch disk out, put it into the dock and have full power, full speed, for the disk.

Why use EXT3 and not EXT4?  EXT4 is what any new file systems should be using today.
Hopefully, you have backups for this data planned.  When an encrypted disk has any sort of failure, there is seldom any way to recover data except from a good, recent, backup.

I don't use KDE or a non-LTS release. Perhaps the GUI tool used is laying down random data before putting the file system down?  That is the more secure choice.  With the **cryptsetup** tool, it is optional.  GUI tools tend to provide 20% of the features of the CLI tools and try to do what 80% of the end-users would want.  Someone going to the effort to encrypt would probably want the most secure setup.

While you were at it, did you setup LUKS to use 2FA for unlocking?  Say, with a yubikey and challenge-response?  This can be added later. There are 8 "slots" for different unlock codes/methods for each LUKS container.

---

### Post by springshades on 2020-01-26
Follow up here. Obviously much later because it took a while to make sure everything worked.

Nothing exciting happened here. It was just a relatively slow drive being put through a long process. No particular power issues. Pulling an external drive out of an external enclosure defeats the entire purpose of getting an external drive in the first place (even though I do in fact have a USB dock). It turned out that the entire 4 TB drive was being written to at a rate of somewhere around 40-50 MB/s. I'm sure there is other software that could have gone faster, but I'm sure it is using dd behind the scenes which has always seemed slower than most other methods.

In the end though, I realized that since it is an external drive that I'm expecting to keep for years, I should really be using something more portable than LUKS anyway. Veracrypt ended up taking a similar amount of time to encrypt the drive.

If anyone reads this thread, make sure to consider portability before going for ext4 as well. The previous post makes it sound like everyone should be using ext4 for everything right now. Sure, it should be used for system drives, but it doesn't work well anywhere besides RECENT versions of Linux. Use ext3 if there is any chance that you'll plug your drive in to Windows or even an older Linux like RHEL/CentOS 6. I mean, ext4 is still actively getting bug fix patches... nice for software, not so nice for a file system. It has certainly existed for a long time, but it has only been the preferred file system of stable operating systems much more recently.

---

### Post by TheFu on 2020-01-26
>  It has certainly existed for a long time, but it has only been the preferred file system of stable operating systems much more recently. 
That depends on what "recent" means.  If it is 12 yrs ago, then  I suppose that could be true.  Around here, very few people run any system older than 16.04.

ext4 has been rock solid for over a decade.  I was a very late adopter, waiting for it to be production ready.  Built a system on 2010 and used ext4 as the primary file system, replacing JFS that was on the prior install, which I'd been using for over a decade before.

I can't imagine anyone using CentOS v6 at home today.  CentOS v8 is current.  In a business, if they are using USB connected disks, then there are other serious issues. Same if they are running RHEL6, though ext4 was the default file system for that release.

You are correct that if connecting a disk to Windows, then portability should be considered.  I find it easier just to never connect storage to Windows. Windows can access Linux storage in many different, secure, ways, like using sftp, scp or if you like pain, NFSv4 with encrypted Kerberos authenticated connections.  Pretty much any other method isn't secure.

---

