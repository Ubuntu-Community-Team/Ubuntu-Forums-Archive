---
title: "Permissions Issue"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Novagenesis on 2006-06-30
Hello.

I have a minor issue with the default mount/umount settings and can't seem to make the change I require.

I have my cd drives set to noauto,user in the fstab.. That part is okay... but when a user mounts a cd drive, only that -same- user can unmount it.

I have a couple users on my home system that have no root access.  I want to keep it that way... and I want any of them to be able to umount the drive.  I can't seem to find that anywhere on google or the umount manpage.  Can someone help me with this?

In case it's important, I'm currently using Dapper 6.06

---

### Post by grooverider on 2006-06-30
according to what i did:
Mounting and unmounting without being root

When you are logged in as root you can do anything but you can also accidently do more than you wanted to. It is therefore better to make the cdrom mountable for ordinary users. To give the privileges to mount a drive to any user you must first log in as root and do 3 things:

make the directory /cdrom world writable 
make the device world writable 
edit the fstab 

To make the directory /cdrom world writable you type (while no cdrom is mounted!): 
#chmod 777 /cdrom	

To make the device world writable you type (use the device name accordingly to your system): 
for the ATAPI cdrom:
#chmod 666 /dev/hdc	
for the SCSI cdrom:
#chmod 666 /dev/scd0	

Now you must edit /etc/fstab and give the permission to mount the cdrom to any user. This is done by inserting the line following line: 

/dev/hdc  /cdrom     iso9660 ro,noauto,user 0 0
In the case of the scsi cdrom this looks like: 

/dev/sdc0  /cdrom     iso9660 ro,noauto,user 0 0
Please note that there might already be a line for the /dev/hdc device (or /dev/sdc0) in this case you have to edit the line and not add a new entry. The line tells Linux on which directory to mount the cdrom and with device to use. It tells Linux also that the file system is iso9660, that it should be mounted read only and that it should never be mounted at startup (when there might not be a CD in the drive). The option "user" means that any user can mount the drive. 

Save the fstab file and log in as normal user. Now insert a CD into the drive and mount it with the command: 
$mount    /cdrom

---

### Post by Novagenesis on 2006-06-30
Sadly, that's not what I need.  I can already -mount- and -unmount- as non-root.  What I -can't- do is:

normaluser1 mounts a cd then logs off.

normaluser2 logs on...can NOT unmount the CD without suing to root.  I trust my other users, but they are not knowledgable enough to be admin and could accidentally do damage

---

### Post by Novagenesis on 2006-06-30
I hate to..but..bump?

---

### Post by Novagenesis on 2006-07-02
Is it not possible to set umount so a non-root user can unmount a disc mounted by another user?

---

### Post by aysiu on 2006-07-02
If all your users are in these groups: ```
dialout cdrom floppy audio dip video plugdev lpadmin scanner
``` then all of them should be able to eject or unmount automounted devices.

---

### Post by Novagenesis on 2006-07-02
[QUOTE=aysiu]If all your users are in these groups: ```
dialout cdrom floppy audio dip video plugdev lpadmin scanner
``` then all of them should be able to eject or unmount automounted devices.[/QUOTE]

Hi..thanks, but this doesn't help.
All my users are already in those groups.

The cdrom device isn't set to auto...should I set my cdrom drives to NOT be noauto? I thought that was "Just Not Done"...

My problem is that if _I_ mount a cd, then log off without unmounting it, my girlfriend cannot unmount it when she logs in.  It says:

umount: only (my_account) can unmount /dev/hdd from /media/cdrom1

Further, in Mtab, my uname is -plastered- as the person who mounted it.  I'd really rather not the potential security risk of ME (not a security guru) writing a scipt to suid root and unmount a cdrom drive.  Is it possible for her (no-root-access) to unmount a cd that -I- mounted, not as su, but as my username?

---

### Post by aysiu on 2006-07-02
I think I get it.

So if you mount a CD in your account, log out, and then your girlfriend logs in, she can **not** eject it.

But if you mount a CD, unmount it, log out, and then she logs in and puts the CD in, she **can** eject it.

Is that correct?

---

### Post by Novagenesis on 2006-07-02
Exactly... I have all the permissions set as several sites claim is correct.  It's just that the pesky mount utility REMEMBERS the name of the person who mounted the cd, and demands they be the unmounter.  Only sudo can override that atm.  And that's the issue.  I was gone for the day once, and I let her use my account (I trust her totally, but she can't remember my insane passwords)...
Gnome froze due to scratch on rented DVD, she reboots, DVD stuck in drive, in her account.

---

### Post by aysiu on 2006-07-02
From [the Tux Files website](http://www.tuxfiles.org/linuxhelp/fstab.html): > **user** and **nouser** These are very useful options. The user option allows normal users to mount the device, whereas nouser lets only the root to mount the device. nouser is the default, which is a major cause of headache for new Linux users. If you're not able to mount your cdrom, floppy, Windows partition, or something else as a normal user, add the user option into /etc/fstab. Maybe *nouser* might help? Or maybe specifying the user IDs? I have no idea what the solution is.

---

### Post by Novagenesis on 2006-07-02
nouser will prevent non-root users from playing with the mount command for the cd at all...

If I change "user" to "user=myusername" it ignores the flag and assumes nouser..and only root can mount

And for teh record, I disabled 'noauto' and tested again....still the same side-effects

Perhaps mount is limited in locking it TO a user?


SOLVED!!!!

Ok, I solved it, and for search purposes, I will place what I found.

The user option is single-user specific to whomever mounts it.

The "users" option, which I have never seen anywhere except buried in a page of the manpage for mount that I hadn't read as well as I guess I should have, will allow ANYONE AT ALL to mount/umount at any time.  Yeehaah

Thanks for the offers of help, and hope if anyone needs the answer, they can find it.

---

### Post by aysiu on 2006-07-02
I think I may have found a solution.

So I have a dummy account that I've set up on my Ubuntu. If I put in a CD in my account and then try to right-click eject it from the dummy account, I get an error saying only my account can eject.

However, if I put the CD in under my account, and then press the eject button (on my actual physical computer), the CD ejects under the dummy account.

In past versions of Ubuntu (Breezy, Hoary, Warty), the eject button would not actually eject CDs (they had to be ejected from within Ubuntu), but as of Dapper, the eject button on your computer should actually unmount and eject the CD.

---

### Post by Novagenesis on 2006-07-03
I installed dapper, and actually the eject button doesn't work for me... I'd like it to, but I'm too lazy to hunt down an answer to that one ;)

---

### Post by aysiu on 2006-07-03
[QUOTE=Novagenesis]I installed dapper, and actually the eject button doesn't work for me... I'd like it to, but I'm too lazy to hunt down an answer to that one ;)[/QUOTE]
That's weird.

In the past, I had to do some kind of weird command-line tweaking or using Automatix to get the eject button to work by itself, but in Dapper, I didn't do that at all.

Well, if it's not working for you out of the box, maybe you can [force it to work.](http://ubuntuforums.org/showthread.php?t=115499)

---

