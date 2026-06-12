---
title: "Hard drive backup preferences"
date: 2009-03-12
forum: General Help
---

### Post by r1ch on 2009-03-12
Hi all,

I am looking at different options for backing up my hard drive and wondered what everyone's preferences were...

... please let me know, **do you back up your Ubuntu installation / Hard drive?**
and if so, [B]what method do you use?
[/B]

At the minute I only use the following guide [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087") and find it does the trick, though trying to get into the backup afterwards is a very slow process.

---

### Post by JBA2337 on 2009-03-12
One of the the simplest backup programs  to use is **sbackup**. Use synaptic package manager and look for **sbackup**.

Lately, I have been using either **linbaku** or **quickstart**. Both of these are easy to use both backup and restore. Linbaku only backs up and restores your entire Ubuntu installation, and it does not have an automatic backup.

Quickstart can backup only your home directory, your system directory, or your configuration files; or all three. Quickstart does have an automatic backup that you can set to backup whenever you desire. Quickstart also includes some other nifty utilities.

Quickstart:
[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

Linbaku:
[http://ubuntuforums.org/showthread.php?t=754816](http://ubuntuforums.org/showthread.php?t=754816)

JBA

---

### Post by r1ch on 2009-03-13
That's good JBA, thanks for the heads up on those.

---

### Post by Tobywuk on 2009-03-13
I use rsync, make an alias for the command and then just quickley run this every time i want to do a backup. could also use this with cron to automate it.

I have three hard drives on my system. one for ubuntu, one for data and a third for backup. rsync just syncs the data hard drive to the backup hard drive. I dont bother with the ubuntu drive as im always formating, upgreading it so i dont find its worth it, most important thing for me is the data.

On my notebook (macbook pro) I just use rsync on my whole home directory to an external USB hard drive.

---

