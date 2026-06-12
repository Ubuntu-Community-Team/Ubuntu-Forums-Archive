---
title: "Low disk space - No longer boots"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Shampyon on 2006-08-18
A day or two ago I started to notice little warnings about the space on / being at 90%. I emptied the trash, I moved some files to different partitions. The number kept going up every time I booted. Eventually it got to 100% while my brother was using it, and there's no longer enough space for it to even start up the GUI.

Wierd thing is, I only have about 1-2GB in my Home folder, and it's a 40GB partition. What could have happened to the other 38GB?

---

### Post by ifishfortorque on 2006-08-18
Check for log files (in /var/log/ for example); if something goes wrong, these can grow like crazy.  Also, you may want to look for security problems (e.g. chkrootkit).

---

### Post by Shampyon on 2006-08-18
I'm still not that good with the ol' command line. What would the commands be to check the log files? I'm assuming just chkrootkit or sudo chkrootkit will be enough for the second option.

---

### Post by ifishfortorque on 2006-08-18
I'll assume you know how to navigate to the folders in question -- depending on what you have installed on your system, you might have logs in different places.  In /var/log/ you could type 

```
ls -l
```

and see if there are any files that are really huge.  

However, you might not need to use a terminal.  I think Nautilus probably has some view whereby you can check how big files are; this would do you just as well.

---

### Post by dannyboy79 on 2006-08-18
Something to think about. One time I thought I was mounting a 300gb partition to a folder located within my home directory (ie /home/daniel/music) but because I had an incorrect fstab entry the partition wasn't getting mounted therefore that music folder only had as much room as the partition that was being mounted at /home which was only 10gb. All of a sudden I was downloading some stuff and it told me it had to stop because the destination drive was full, I am like, no f___ing way!!!! Looked into it and as I stated the huge partition wasn't getting mounted therefore music folder was using the partition that /home used. That's probably not your problem but I thought I'd bring it up just in case! I got in the habit of viewing my dmesg more often as well due to that!

---

### Post by teasum on 2006-08-18
Another item to check is whether you have backup files building up in /var.  I installed the simple backup program from automatix, and then let it run for a while.  The default settings wrote the backups to /var/backups, I think, and after a week, I almost ran out of space on my / partition.  After I figured this out, I just moved the bacup directory (and files) to my /home partition, which has plenty of space.  This might not apply to you at all, but I thought I'd put it out there just in case.

---

### Post by backdoc on 2006-08-18
> I'm still not that good with the ol' command line. What would the commands be to check the log files? I'm assuming just chkrootkit or sudo chkrootkit will be enough for the second option.

The first place I would look would be /var/log.  The second place I would look would be for a temp directory where you might be ripping movies or something and not deleting the ISO.  From a shell, try:

cd /var/log
Once you're there, ls -l will show the file sizes, ls -lh will show them in "human" readable sizes (MB's)
Also, I use du (disk usage) alot with the -chs options, it will show you how much disk space is being used.  Just try it from /home and /var and eventually you can narrow it down.

As you are navigating around, you might find it helpful to use cd - <enter>.  That's a cd command, a space and then a dash, followed by <enter>.  It will take you back to the last directory you were at.  That and tab completion are invaluable on the command line.  Try tapping tab twice.

[edited]
I forgot the most useful command of all, 'df -h'.  That means "disk free, in human readable form".  It will return results like:

Last login: Sun Aug 20 15:15:45 2006
dapper-desktop@~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              25G  3.6G   20G  16% /
varrun                506M   84K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  112K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/sda7              49G   21G   26G  46% /mnt/LinuxDocs
/dev/sda1              20G  8.8G   11G  45% /mnt/winC
/dev/sda2              98G   38G   60G  39% /mnt/winD
/dev/hda              650M  650M     0 100% /media/cdrom0

[end edited section]

---

### Post by Shampyon on 2006-08-18
Thanks for the help so far, folks. You've made it pretty darn easy to understand.

Your advice has helped pinpoint the major culprits, and I've managed to clear just enough disk space to enable the gui, which in turn has made is super-easy to get rid of the huge amount of unneeded backup files.

The problem, as usual, was one silly mistake I'd made a long time ago and simply forgotten about:
I'd set the Simple Backup tool to back up /etc, /var, /home and /usr/local once a week. I never got rid of the older backups.

Simple problem, simple solution. Thanks to your help, my PC's back to fully operational.
=D>

---

