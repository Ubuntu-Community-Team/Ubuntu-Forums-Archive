---
title: "Moving installation to new disk - Old disk has bad sectors"
date: 2009-04-23
forum: General Help
---

### Post by super_czar on 2009-04-23
So  have a Ubuntu based hme server that I have spent 100 hours configuring over the last two years

Disaster struck this morning when the server started acting up
A disk SMART check revealed bad sectors on the primary 80GB IDE disk

So I went ahead and gt a new 500GB SATA disk

Now I'd like to clone the existing install (the existing install works, but the disk may die any moment) 

What would be the best way to clone this install to th enew disk
The ideal tool should be capable of skipping the bad sectors as much as possible

---

### Post by stwschool on 2009-04-23
Best bet is to backup all your files (complete with permissions) this way:

tar cvpzf /backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/media --exclude=/sys /

What that does is make an archive at /backup.tgz of everything in / excluding the things tagged --exclude (very important to tag the backup archive itself). Put the backup file somewhere nice, an external hard drive or something like that.

Once that's done, grab an ubuntu disk and run a standard install with the new hd plugged in (keep the old one around just in case it doesn't work) and then extract the contents of the archive into your main hard drive (sudo tar xvpzf backup.tgz -C /) and all should be well after a restart.

---

### Post by super_czar on 2009-04-23
hmm, but what when tar encounters the bad sectors?
Is it going to skip em, or would it stall

---

### Post by stwschool on 2009-04-25
Sorry forgot all about the thread. Not sure to be honest. It usually reports any errors it finds so the best thing to do is try it and if it doesn't give errors you're ok. If it does, try again.

---

### Post by aaronmarsh632 on 2009-04-25
I wouldn't recommend 'cloning' from the hard drive with bad sectors because even if all the data copied over, you may find some of the data will be corrupt due to the bad sectors.

It's a pain in the **** but id suggest - start again. try and use as much data as you can from your old hard drive, but try not to completely rely on it.

and of course, once you have your new setup finished, create a backup on a dvd for future security.

---

### Post by super_czar on 2009-04-27
> **aaronmarsh632 said:**
> I wouldn't recommend 'cloning' from the hard drive with bad sectors because even if all the data copied over, you may find some of the data will be corrupt due to the bad sectors.

It's a pain in the **** but id suggest - start again. try and use as much data as you can from your old hard drive, but try not to completely rely on it.

and of course, once you have your new setup finished, create a backup on a dvd for future security.

you were right Aaron, after wasting hours cloning the disk and restoring grub, the new copy had the same problems...

I eventually had to start from scratch, using bits & pieces from the already configured .conf files from what i already had..thankfully, the setup time was just a few hours this time minus the learning curve when doing it the 1st time

needless to say, 1st thing post configuring : i backed up the new system using sbackup

---

