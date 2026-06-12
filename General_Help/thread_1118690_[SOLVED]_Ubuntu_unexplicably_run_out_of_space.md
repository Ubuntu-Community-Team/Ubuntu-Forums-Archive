---
title: "[SOLVED] Ubuntu unexplicably run out of space"
date: 2009-04-07
forum: General Help
---

### Post by LoneSt4r on 2009-04-07
Hello!

This is a problem I am consistently faced with since Gutsy.  Everything runs smoothly for months, then my root partition gets filled in a matter of hours.

My root partition is 19G.  I did a clean install of Intrepid about a month ago and the occupied data remained constant around 4.8G until I upgraded to Jaunty, whcih used about 6.3G.

This morning, I wake up and the whole 19G is used!

I want to repeat that this happened to me on Gutsly, Hardy, Intrepid, and now Jaunty.  I resized my root partition from 10G to 15G to 19G, but that only delays the problem.

I tried solving the problem with :

- sudo apt-get clean
- sudo apt-get autoclean
- sudo apt-get autoremove

Those commands freed a tiny amount of space (~500M).

Find my system info below.  Know that the space used by /mnt and /home are located in other partitions.

fstab:

proc            /proc           proc    defaults        0       0
/dev/sda1       /mnt/Windows    ntfs    users,umask=0222,ro     0       0
# /dev/sda2
UUID=3d63e813-a8ff-4971-a444-261d37d8d686 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=e8c7376d-42f8-478b-84eb-7791705b9777 /home           ext3    relatime        0       2
# /dev/sda3
UUID=ddd82d2f-5df7-48dc-afd5-032bcb824a9e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sdb1       /mnt/Backup     ext3    relatime        0       2
/dev/sdb2       /mnt/Transport  fat32   default         0       0
/dev/sdb3       /mnt/PAL        ext2    relatime        0       0

root@:/# df -h
Sys. de fich.            Tail. Occ. Disp. %Occ. MontÃ© sur
/dev/sda2              19G   18G     0 100% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  236K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  108K  501M   1% /dev
tmpfs                 501M  2,0M  499M   1% /dev/shm
lrm                   501M  2,4M  499M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1              15G  8,2G  6,5G  56% /mnt/Windows
/dev/sda4             197G  119G   68G  64% /home
/dev/sdb3             623G  273G  318G  47% /mnt/PAL


root@:/# du -hc --max-depth=1
0       ./sys
48K     ./tmp
312M    ./lib
2,1M    ./dev
0       ./proc
4,0K    ./selinux
4,0K    ./opt
8,0M    ./root
37M     ./boot
402M    ./var
119G    ./home <-- on another partition
3,9G    ./usr
4,0K    ./srv
294G    ./mnt <-- on another partition
17M     ./etc
6,1M    ./bin
12K     ./media
7,6M    ./sbin
16K     ./lost+found
417G    .
417G    total

From those outputs, I cannot find the missing 13G...  Could it be that Ubuntu does not count things right?  I would be surprised if that were the case...

Anyone with a solution?

Thanks!

---

### Post by ryanhaigh on 2009-04-07
Using max-depth with the du command limits the depth which it reads into the file hierarchy so you are not really getting the info you are looking for from that command. Try running it again without the max-depth argument or you can use the disk usage analyser to find where files consuming your disk space are. 

Just a guess (based on someone else on here having a similar problem) but I would check the size of the log files in /var/log

---

### Post by LoneSt4r on 2009-04-08
> **ryanhaigh said:**
> Using max-depth with the du command limits the depth which it reads into the file hierarchy so you are not really getting the info you are looking for from that command. Try running it again without the max-depth argument or you can use the disk usage analyser to find where files consuming your disk space are. 

Just a guess (based on someone else on here having a similar problem) but I would check the size of the log files in /var/log

Good morning!

The "max-depth" option is only used for output display purposes.  I tried it on my /usr directory and I received the same bottomline result with or without the option.  I get the same 3.8 Gb I see in my original post.  I did repeat the test with the Disk Analyser tool, but I believe it is just a GUI for the du command...

The total size of my /var/log directory is 14 Mb.

I am starting to wonder if there could be a problem with the partition allocation table, the table the reporting accurately the free space on my partition.  Has anyone seen something like that happen or could anyone suggest a way to test this?

Any other suggestion is obviously very welcome...

Thanks!

LoneSt4r

---

### Post by aesis05401 on 2009-04-08
Have you seen this thread : _[http://linux.derkeiler.com/Newsgroups/comp.os.linux.misc/2008-12/msg00174.html]("http://linux.derkeiler.com/Newsgroups/comp.os.linux.misc/2008-12/msg00174.html")_?

There are a number of suggestions if you follow the thread, including listing processes holding orphaned files with this command:
```

lsof | (sed 1q; grep deleted)

```

Either way, the explanation of why df and du report different totals is in the linked post.  Good luck!

---

### Post by kyphi on 2009-04-08
If you are using a backup program then your root directory will fill up unless you configure it to delete superseded backups more frequently or specify a different location for saving them.

To show file system usage use

df -h

That will let you identify by looking at the percentages what space is being used.

To identify large files in the root partition use this command 

sudo find / -type f -size +100000k

You can vary the size parameters.

After that it is just a matter of deleting the excessive files.



(code tags are not functioning)

---

### Post by aysiu on 2009-04-08
You might want to install and use FileLight to find out exactly what's taking up so much space.

---

### Post by LoneSt4r on 2009-04-08
> **kyphi said:**
> If you are using a backup program then your root directory will fill up unless you configure it to delete superseded backups more frequently or specify a different location for saving them.

No, I am not using any backup software.  I do my backup on another partition (on another physical hard drive) using the rsync command and crontab.  As you can see from my original post, I did try the other commands you are suggesting.

> **aysiu said:**
> You might want to install and use FileLight to find out exactly what's taking up so much space.

Thanks for the suggestion, but I don't believe it will show more than the Disk Analyzer tool did...  Looks like it has a nice GUI, though!

> **aesis05401 said:**
> Have you seen this thread : _[http://linux.derkeiler.com/Newsgroups/comp.os.linux.misc/2008-12/msg00174.html]("http://linux.derkeiler.com/Newsgroups/comp.os.linux.misc/2008-12/msg00174.html")_?

There are a number of suggestions if you follow the thread, including listing processes holding orphaned files with this command:
```

lsof | (sed 1q; grep deleted)

```

Either way, the explanation of why df and du report different totals is in the linked post.  Good luck!

Thanks, I will make sure to bookmark that link!  After reading it carefully, the problem with orphaned files is supposed to clear itself after rebooting.  That is not the case with me.

However, I believe you sent me in the right direction.  I will keep on investigating.

Here is the output of the command you suggested.  No file above 500k is reported.

```
COMMAND     PID USER   FD   TYPE DEVICE   SIZE NLINK    NODE NAME
gnome-key  3162   jp  txt    REG    8,2 588096     0 1116258 /usr/bin/gnome-keyring-daemon (deleted)
gnome-set  3285   jp  txt    REG    8,2  34744     0 1124155 /usr/lib/gnome-settings-daemon/gnome-settings-daemon (deleted)
trackerd   3314   jp  txt    REG    8,2 187852     0 1125765 /usr/lib/tracker/trackerd (deleted)
tracker-a  3315   jp  txt    REG    8,2  39100     0 1117659 /usr/bin/tracker-applet (deleted)
update-no  3320   jp   22r   REG    8,2    456     0  554864 /var/lib/update-notifier/user.d/firefox-3.0-restart-required (deleted)
tracker-i  3359   jp  txt    REG    8,2  72332     0 1125767 /usr/lib/tracker/tracker-indexer (deleted)
compiz     3446   jp   10r   REG    8,2  12206     0 1117793 /usr/bin/compiz (deleted)
compiz.re  3497   jp  txt    REG    8,2 216048     0 1117789 /usr/bin/compiz.real (deleted)
compiz-de  3500   jp   11r   REG    8,2   3139     0 1117787 /usr/bin/compiz-decorator (deleted)
gtk-windo  3502   jp  txt    REG    8,2  80744     0 1117786 /usr/bin/gtk-window-decorator (deleted)
firefox   12336   jp   48u   REG    8,2      0     0  537568 /var/tmp/etilqs_LLfVKcTQb7wgEP0 (deleted)
```

In the meantime, if you have another command I could use to identify the datafiles that lost their names, feel free to enlighten me!

LoneSt4r

---

### Post by drs305 on 2009-04-08
LoneSt4r,

The du results look about normal except for the two that you say are mounted elsewhere. One thing to check is that there aren't files hidden under those mount points. Unmount whatever you have mounted on /mnt and see the /mnt folder is still empty. It's possible it has files stored on the mount point instead of on the other device. You wouldn't necessary see them in the folder if you had another device mounted.

---

### Post by LoneSt4r on 2009-04-08
> **drs305 said:**
> LoneSt4r,

The du results look about normal except for the two that you say are mounted elsewhere. One thing to check is that there aren't files hidden under those mount points. Unmount whatever you have mounted on /mnt and see the /mnt folder is still empty. It's possible it has files stored on the mount point instead of on the other device. You wouldn't necessary see them in the folder if you had another device mounted.

I'll be damned!  You nailed it!  Thank you!!!

My /mnt/Backup folder was containing 16G.  Most likely, my external drive failed at some point and the backup did not go there, but in the folder normally supporting the mount!

Everything is back to normal...  Thanks again!

```
Sys. de fich.            Tail. Occ. Disp. %Occ. Monté sur
/dev/sda2              19G  4,8G   13G  28% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  240K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   88K  501M   1% /dev
tmpfs                 501M  2,0M  499M   1% /dev/shm
/dev/sda4             197G  119G   69G  64% /home
overflow              1,0M  956K   68K  94% /tmp
```

---

