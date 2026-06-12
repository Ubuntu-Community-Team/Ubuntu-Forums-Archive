---
title: "Backing up data?"
date: 2008-12-27
forum: General Help
---

### Post by fiel on 2008-12-27
I have plenty of pictures, school work, and other files I plan on backing up for safe keeping.  Although I have several questions about doing this.

Is there any danger (long term/short term) if I place everything into a single folder and compress it up into 1 file?  Is there any advantages between using zip, tar.gz, or 7z?  

Most of the files I want to keep in storage for long term.

---

### Post by squaregoldfish on 2008-12-27
Assuming you've got one hard drive on your computer, making backups on the same drive as the original data is not going to help - when the drive breaks (it will break - it's just a matter of time), you'll have lost both copies. You could install a second hard drive for the backup, but if something fries the whole computer, you'll have the same problem.

The most reliable way of backing stuff up isn't the cheapest, but it goes something like this:

1. Buy two external hard drives, big enough to hold all the data you want to back up for the foreseeable future (no point having to buy new drives in 6 months' time).

2. Back up your files onto both drives, and store one away from your computer, i.e. in another building. There's not much point keeping a backup in your house if it burns down, or someone breaks in and takes yout computer and the backup drive.

3. Every few days, or every day, depending on how you feel, update the backup drive you keep in your house.

4. Every few weeks, swap the off-site backup drive with the local one.

That's what I do. It has the added advantage that if I accidentally delete a file I need, I've got two chances to retrieve it.

Depending on how much you want to back up, you might also consider making use of online storage services. I've never used them myself, but it's definitely an option, depending on how much you trust the company to keep your data secure and not lose it. (A UK ISP accidentally wiped 700Gb of user emails a couple of years back. Not good.) No idea what costs are like either.

Steve.

---

### Post by mtopro on 2008-12-27
I agree completely with squaregoldfish.  I do the same thing with my data and some external hard drives.

The idea of zipping them could make it more difficult to back up.

I use RSYNC to back up the data.  It is pretty easy to setup a text script to run your backups for you.  RSYNC will compare data and only update the files that have changed or been added.

A good reference for RSYNC can be found at: [http://rsync.samba.org/ftp/rsync/rsync.html]("http://rsync.samba.org/ftp/rsync/rsync.html")

---

### Post by fiel on 2008-12-27
Well at the moment I 2 external drives that I will be backing up data to.  

Most of the data I will be backing up is mostly school work, that at the moment I have no need for but would like to have in storage.

For files I won't likely be needing in the next few months, is it safe to zip them up for long term storage?

---

### Post by squaregoldfish on 2008-12-27
I'd advise against zipping the files up. If you back up 10 files separately, and one gets corrupted, you've lost one file. If you zip those files, and get corruption, you lose all of them.

As mtopro says, rsync is the tool of choice for backups. Keeping all the directory structures and whatnot identical on your backups makes it really simple to retrieve your data later on - everything's in exactly the same place as it was on the original machine.

Steve.

---

### Post by albinootje on 2008-12-27
> **fiel said:**
> I have plenty of pictures, school work, and other files I plan on backing up for safe keeping.  Although I have several questions about doing this.

Is there any danger (long term/short term) if I place everything into a single folder and compress it up into 1 file?  Is there any advantages between using zip, tar.gz, or 7z?  

Most of the files I want to keep in storage for long term.

Can you tell us what the filesystem on your external disks are ?
If you use FAT32 you should realise that all files will end up as "executable", which looks a bit ugly imho (cough), and can be impractical when restoring from backups.

I would recommend grsync for this.

The many options in grsync might seems overwhelming at first, but the defaults are pretty OK.

Make sure you get a deb package for the latest release, because afair the grsync deb in Hardy has an innocent but little annoying bug for the "session" naming.

And in general, rsync is super-cool, but be very careful with using the rsync --delete parameter, one typo or mistake with that included can be disastrous.

---

### Post by fiel on 2008-12-27
> **albinootje said:**
> Can you tell us what the filesystem on your external disks are ?
If you use FAT32 you should realise that all files will end up as "executable", which looks a bit ugly imho (cough), and can be impractical when restoring from backups.

I would recommend grsync for this.

The many options in grsync might seems overwhelming at first, but the defaults are pretty OK.

Make sure you get a deb package for the latest release, because afair the grsync deb in Hardy has an innocent but little annoying bug for the "session" naming.

And in general, rsync is super-cool, but be very careful with using the rsync --delete parameter, one typo or mistake with that included can be disastrous.

Well I'm dual booting between XP and Ubutnu (using ext2).  As for my external drive, It's FAT32.

I will look into this rsync and grsync, but will the filesystem type matter?

---

### Post by albinootje on 2008-12-27
> **fiel said:**
> Well I'm dual booting between XP and Ubutnu (using ext2).  As for my external drive, It's FAT32.

I will look into this rsync and grsync, but will the filesystem type matter?

As I already tried to explain, copying to FAT32 partitions will make your files (don't know about directories) all executable.

FAT32 is from the FAT family, it's an ancient and very primitive filesystem from the DOS period of time.

I find that ugly to work with in Linux, but another thing is that if someone else has access to your home directory, then that user can read and write to your files.

I assume that you are the only user on your machine, and you talked about documents and data, not about settings/preferences files, but let's look at an example.
GPG or GnuPG can be used for email encryption (and file encryption).
It will normally put the secret key in the .gnupg/ directory with such permissions that other users who can go into your home directory still cannot read it.
If you would back up to a FAT32 partition and then restore everything, those other users *can* read and copy your secret key.

---

### Post by jerome1232 on 2008-12-27
Another reason I wouldn't compress them is generally people's space eaters are music and pictures which are already in compressed formats, so compressing them again won't actually make them any smaller.

If you are backing up to a Microsoft file system (fat,ntfs) then you probably do want to tar (archive, not  compress) the files up though because that will preserve their permissions.

Other than that I agree whole heartedly with using rsync in a small backup script.

---

