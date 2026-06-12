---
title: "Why do I get this error message?"
date: 2009-04-20
forum: General Help
---

### Post by funky_uncle on 2009-04-20
I'm trying to make a backup of my /home/username before I install a second distro. However, I get this:[IMG]http://img205.imageshack.us/img205/3734/screenshot1q.png[/IMG]and obviously, the file IS there. So why am I told it's not?

---

### Post by albandy on 2009-04-20
The ISO format don't allow you to copy some kind of file names
Instead of copying it directly, package it and then copy it to your CD

---

### Post by funky_uncle on 2009-04-20
> **albandy said:**
> The ISO format don't allow you to copy some kind of file namesAh. Ubuntu really should've said that, then, instead of lying about the file not existing.

> **albandy said:**
> Instead of copying it directly, package it and then copy it to your CDI try creating an archive of it, but:> An error occurred while adding files to the archive.

Permission deniedwhich is weird because I DO have access to them normally.

---

### Post by aeiah on 2009-04-20
i had that problem trying to backup my whole ~/ drive (well, all of it except music and movies).

i was too lazy to find a sane way to do it so i did it with a livecd in the end.

---

### Post by albandy on 2009-04-20
ok, so you want to backup your home ?
simply type
sudo tar zcvfp /tmp/myhome.tgz /home/myusername
then copy the file /tmp/myhome.tgz to the CD

---

### Post by funky_uncle on 2009-04-20
> **albandy said:**
> ok, so you want to backup your home ?
simply type
sudo tar zcvfp /tmp/myhome.tgz /home/myusername
then copy the file /tmp/myhome.tgz to the CDThanks, it's packing the stuff up now in the background. I wonder when I install a new distro, if my settings and plugins for Firefox will be the same. Or must I reinstall them?

---

### Post by aeiah on 2009-04-20
firefox settings are in .Mozilla, which is in your home directory so yes you should be fine. you'll want to make sure you use the same username next time to avoid permission complications though

---

### Post by philinux on 2009-04-20
> **funky_uncle said:**
> Thanks, it's packing the stuff up now in the background. I wonder when I install a new distro, if my settings and plugins for Firefox will be the same. Or must I reinstall them?

I have home on it's own partition which makes reinstalling a doddle.

---

### Post by funky_uncle on 2009-04-20
I ran out of space... :/
I didn't want to include all my music (hundreds of GBs) anyway, since I have it on CD already. But I don't know how to make the backup with all files *except* certain directories. Not from the command line. Maybe I'll just do like aeiah and make the backup from a live CD.

> **philinux said:**
> I have home on it's own partition which makes reinstalling a doddle.That's what I'm looking for :)
As long as I take care not to delete any of the other partitions when I install a new distro, I should be OK, yes?

---

### Post by CatKiller on 2009-04-20
> **funky_uncle said:**
> and obviously, the file IS there. So why am I told it's not?

Because it's not a file. I believe it's a symlink to something that isn't there. Its only purpose is to be removed on a clean shutdown of Firefox, so that if Firefox isn't running, and that file is still there, then the last shutdown wasn't clean and Firefox should ask to restore your session from last time. Backing it up makes no sense whatsoever. Either skip that file in your backup, or don't backup that folder when Firefox is running.

---

### Post by albandy on 2009-04-20
> **funky_uncle said:**
> I ran out of space... :/
I didn't want to include all my music (hundreds of GBs) anyway, since I have it on CD already. But I don't know how to make the backup with all files *except* certain directories. Not from the command line. Maybe I'll just do like aeiah and make the backup from a live CD.

That's what I'm looking for :)
As long as I take care not to delete any of the other partitions when I install a new distro, I should be OK, yes?

add --exclude dir_to_exclude at the end of the tar command, for example:

tar zcvfp /tmp/myhome.tgz /home/myusername --exclude "/home/myusername/mymusicfolder"

---

### Post by funky_uncle on 2009-04-20
Oh... I thought it was the file that contains my personal profile for Firefox.

---

### Post by funky_uncle on 2009-04-20
> **albandy said:**
> add --exclude dir_to_exclude at the end of the tar command, for example:

tar zcvfp /tmp/myhome.tgz /home/myusername --exclude "/home/myusername/mymusicfolder"That seems to work, but how do I use the exclude command on several different subfolders? I'm trying to run ```
sudo tar zcvfp /tmp/funkybackup.tgz /home/funky --exclude /home/funky/Music --exclude /home/funky/incoming --exclude /home/funky/Themes
``` but it doesn't seem to work on all the folders.

---

### Post by CatKiller on 2009-04-21
> **funky_uncle said:**
> Oh... I thought it was the file that contains my personal profile for Firefox.

The profile folder is, yes. But the lock file is just a lock file.

---

