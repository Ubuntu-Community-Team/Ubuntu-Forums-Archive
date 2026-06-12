---
title: "Move home directory?"
date: 2006-07-11
forum: Desktop Environments
---

### Post by ironfistchamp on 2006-07-11
Is this possible. I have been using Dapper for a number of months now and think I should move my home dir to another partition. 

I hav someone where to put it and I have mounted it. How can I copy the entire /home to this new place?

Thanks

Ironfistchamp

---

### Post by taurus on 2006-07-11
One way is to boot into recovery mode (single user mode) from GRUB menu.  Mount the new directory where new home would be someplace (not /home right now).  Then, copy current /home to that new partition.  Unmount both current /home (if it's on a seperate partition) and new /home.  Edit /etc/fstab to reflect the new /home.  Reboot...

---

### Post by aysiu on 2006-07-11
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by ironfistchamp on 2006-07-11
SHAZAM...I shall try this asap.

I really don't like gparted.It just doesn't seem to do what I want. I can't manipulate the things I want. I wanted to delete a partition which is in an extended one. I don't understand all the ins and outs of hard drives. Anyway long story short I couldn't.

However using Partition magic I can do what ever I want. Sure it's not always a good thing but at least it gets done.

Thanks

Ironfistchamp

---

### Post by aysiu on 2006-07-11
I don't like GParted either. I always use DiskDrake instead (requires the download of a PCLinuxOS CD, but it's worth it).

---

### Post by ironfistchamp on 2006-07-11
Sorry how exactly do I get it?

It does sound pretty good.

---

### Post by aysiu on 2006-07-11
Well, a lot of Linux live CDs come with partitioning programs. 

Knoppix, for example, comes with QTParted.
Ubuntu, as you know, comes with GParted.

Well, there's another distribution (based on Mandriva) called PCLinuxOS. It's a live CD, too, and its partitioning program is called DiskDrake.

[http://www.pclinuxos.com/news.php](http://www.pclinuxos.com/news.php)
[http://www.pclinuxos.com/page.php?7](http://www.pclinuxos.com/page.php?7)

---

### Post by thegnark on 2006-07-11
1. mount /home as /media/homeold
2. mount new partition as /home in fstab
3. copy /media/homeold to /home

---

### Post by ironfistchamp on 2006-07-12
Thank you. My main worry was not copying everything over. I wass worried that some important configuration files might not get copied. How much of a danger is that.

---

### Post by Gustav on 2006-07-12
you should do the copying with the -a switch (cp -a source target), It makes sure all permissions and so on is preserved.

---

### Post by ironfistchamp on 2006-07-12
Thanks I shall try that in a minute. :D

---

### Post by ironfistchamp on 2006-07-12
Ok after everything copied I check the files. There seem to be less files and fewer Gb. Here is the strange part. In alot of folders there are less files but over all more bytes. How can that be?

I am copying from ReiserFS to FAT32. Does that matter?

Thanks

Ironfistchamp

---

### Post by aysiu on 2006-07-12
Home can't live on FAT32! Yikes... you didn't reformat the FAT32 partition to Reiserfs or Ext3?

---

### Post by ironfistchamp on 2006-07-12
WOAH thanks for the correction there. Silly friend said I could. Well that right royally buggers up my plan. I need that dir to be read by Win and Lin. Dang.

Any ideas on what I could do with regard to making it readable and writeable by all?

Thanks

Ironfistchamp

---

### Post by aysiu on 2006-07-12
Yes. [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by ironfistchamp on 2006-07-13
Wow thanks very much I shall get right on that when I get back from College.

---

### Post by meatbop on 2006-07-14
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

I'm planning to follow these instructions, but wanted to ask why we have to pipe the output of *find* to *cpio* with the command...

```
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```

... rather than use a simpler *cp* command?  I'm on a Windows box at work just now and can't experiment with my own till tomorrow night.  The only thing I can think of is that *cp* will not accept multiple wildcards, ie * for all files and .* for all hidden files.  What am I missing here?

---

### Post by aysiu on 2006-07-14
My guide is just a more spelled-out and screenshot-driven version of [this guide](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/), which explains it this way: > Since the &#8220;/home&#8221; directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely. Therefore, we use something we learn from the Debian archiving guide18:

---

### Post by meatbop on 2006-07-17
Thanks for the link.

I need to learn more about how linux sees and links data I think, but my little dig into TFM to understand that command was fun.

I'm liking linux a lot, I think I'll stay this time.

---

### Post by teasum on 2006-07-22
I just tried moving my /home directory from hda2 to its own partition (hda7) following aysiu's guide.  Everything seems to have copied correctly, but upon reboot, all my settings are gone.  Desktop backfround, gnome-panel, nautilus, etc., are all back to defaults.    

My newly copied /home folder has 1016 items, while my /home_backup folder has 1028.  I don't know if that makes any difference.  As I said, it looks like all the settings and config folders are in there.  Is there any way to restore the settings, or should I try to restore my old /home folder?

Thanks in advance.

---

### Post by aysiu on 2006-07-22
I would try copying over certain folders one by one and seeing if it makes a difference.

For example, try this, for starters: ```
mv /home/.nautilus /home/.nautilus.old
cp -R /home_backup/.nautilus /home/.nautilus
``` Log out and log back in again and see if any changes happened...

---

### Post by teasum on 2006-07-22
I copied just the .nautilus folder from /home_backup to /home (modifying the command to $mv /home/<username>/.nautilus /home/.nautilus.old, etc.), and one small item changed--the nautilus extension to open a terminal in the selected directory).  Optimistic, I then proceeded to copy the rest of the hidden folders and files manually from the backup file.  Now, it seems that some things are back in order: gkrellm launches automatically at startup, firefox has its profile back, and the OpenOffice.org Quickstarter shows up in the notifications area.  However, my gnome panel settings are still at default, the default human theme is still there, and gkrellm is back to its default skin.  (I list all these not as a complaint but rather as detail for troubleshooting the problem.)

Any ideas on where to go from here?

---

### Post by aysiu on 2006-07-22
Well, if that's looking good, try one by one copying these folders over as well:
~/.metacity
~/.gnome
~/.gnome2
~/.gconf
~/.gconfd

---

### Post by teasum on 2006-07-22
This process of copying one folder at a time via the command line seems to work.  My gnome-panel is back, and my theme.  I think I need to re-copy several other folders as well to get everything back to 100%.  However, I have two questions:

1) is there a way to automate copying each folder via the command line, rather than typing each folder name each time?
2) Is there a reason why the first copy command (find . -depth -print0 | sudo cpio --null --sparse -pvd /new/) didn't copy everything?

Once again, I'm not asking to complain, but rather to see if there is another way to do this, or another command that would work better.

Thanks again!

---

### Post by aysiu on 2006-07-22
Well, theoretically, that tutorial should have automated the process. I think to be safe you should just copy those folders and the folders for your email and web programs and leave it at that.

---

### Post by teasum on 2006-07-23
Thanks for the help.  I manually moved a bunch of folders, and all seems to be well.  Now, on to other adventures in partitioning...

---

