---
title: "installing aps on second drive"
date: 2010-02-11
forum: Desktop Environments
---

### Post by degarb on 2010-02-11
I don't see way to see how much space is used to be used with items to install in snaptic package manager.

More importantly, an install doesn't even ask where i want it installed!    In windows, I can simply add a drive, move the program directories to it. and reinstall if needed to fix any configuration errors.   

What is procedure for adding a new drive, or jump for installing aps?   

I want to buy a jump drive for the notebook, and try new games and aps. but only install the crap on the jump, so as not to fill up my tiny notebook drive.   I am happy with essential stuff on hd.  I can just back up the jump to my external xp terrabyte drive, and not worry about failure.   

Off my topic, but maybe there is some alternatives that could be used, than typical jump drive that would have a longer life.

---

### Post by warp99 on 2010-02-11
If your want to add more space you would just add the drive, then change the mount point to the new drive. For instance I have a netbook with a very small internal drive so I added a larger SD flash drive then mounted my home directory to the new drive. Here's how mine is set up:

```
~$ df -h |grep dev/sd
/dev/sda1             3.7G  3.3G  197M  95% /
/dev/sdb1             7.3G  1.8G  5.2G  26% /home
```

If you notice my main drive is almost full, but the /home directory is mounted to the second drive for all of my personal files. You can also reclaim space by cleaning up packages and installing localepurge:

[http://www.ehow.com/how_2251696_clean-up-packages-ubuntu.html](http://www.ehow.com/how_2251696_clean-up-packages-ubuntu.html)

More information on mounting a second partition as home can be found here:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Linux only sees the file system, not drives. So your /home directory can be moved to the partition on the second drive and the system will still see only one big file system.

---

### Post by degarb on 2010-02-13
Thanks!  Will you be my new best buddy?  At least until I figure this one out.


1.  Is there an easier way to move the home directory?  Something more graphical?

2.  Now, if I move it to a jump, back the jump up, then the jump fails;  is there some finger print that would make Ubuntu not mount the new jump drive as the home?

3.  I really wish to move the installed programs and related files to a jump drive (any usb device I can practically hook up and keep this a notebook).  And perhaps the temp dir.  

This is easy in windows.  Considering many of us ubuntu users are on limited machines, this should be in especially made easy.  Hopefully by next release.

---

### Post by warp99 on 2010-02-15
> 1. Is there an easier way to move the home directory? Something more graphical?


You can use the command "gksudo nautilus" to start a root version of the file manager to move the files if you prefer. It's not too difficult using the command line if you follow the guide. In fact it's actually easier since you only need to cut and paste commands instead of me explaining how to do something with a bunch of dialog boxes buried X number deep.

> 
2. Now, if I move it to a jump, back the jump up, then the jump fails; is there some finger print that would make Ubuntu not mount the new jump drive as the home?

If you read the guide on changing the home directory if you remove the fstab entry to the new home directory it will revert back the the old location.

> 
3. I really wish to move the installed programs and related files to a jump drive (any usb device I can practically hook up and keep this a notebook). And perhaps the temp dir.

If your laptop has a sd card slot you can buy a card, you can get 8 gigs at newegg.com for less than $20 shipped, and move you home directory there. If more room is need you can make a symbolic link from one directory to another on the new card and Linux will follow the link and use the files on the sd card as if it was on the internal drive. As for the temp directory you can mount the tmp directory as tmpfs which will only use system memory. You only need to add a line to your /etc/fstab file like this:

```
tmpfs /tmp tmpfs defaults,noatime,nodiratime 0 0

```

This is exactly how I have my netbook setup since it allows me to retain all of my games/programs without having to swap a drive in and out just to play games. It makes the netbook into a notebook with regards to space.

Edit: If you boot to a Ubuntu live CD or USB you can format the new card and change your home directory much easier than using the guide. I can help you with this if needed.

---

### Post by warp99 on 2010-02-15
And to answer your original question about the size of downloaded applications in Synaptic just highlight the package you want to install, then right mouse click and choose "properties". On the second to last line you'll see that info.

---

### Post by jken146 on 2010-02-15
Also be aware that ```
sudo apt-get clean
``` will free up some space by removing packages from apt's cache (the files that were downloaded and are left over after the installation).

Oh, and to respond to the original question about not being asked where things are installed: you can't just unpack a package wherever you like and expect it to work!  An app in linux is not a self-contained entity like it is in Windows -- it can't be moved around arbitrarily as one 'blob'.  When a package gets installed, parts of it will end up in /usr, other parts in /lib, maybe some in /etc, ...  There are better explanations than this. Use your google-fu if you're interested.

A better way to manage disk space is to keep /home on a separate partition (or a separate disk) from the rest of the file system.  /home contains all the users' files, which is almost certain to make it the biggest directory you've got.

---

### Post by warp99 on 2010-02-15
You could also just make symbolic links to offload files to another disk. Here's something I did very recently to offload some files:

I used the disk usage analyzer tool to determine which folders I could offload. After it finished it appeared the folder /opt would be a good choice since there were some third party programs installed that could be moved very easy. Since I had /home already setup on a separate drive I used that directory for the files and placed a symlink to those files.

I first copied all the files to the home directory:

```
sudo cp -a /opt /home/
```

Verified that the files were copied:

```
ls -R /home/opt
```

Deleted the original /opt directory:

```
sudo rm -r /opt
```

Then made a symlink from /opt to /home/opt:

```
sudo ln -s /home/opt /opt
```

I check my disks:

```
df -h |grep dev/sd
/dev/sda1             3.7G  3.0G  520M  86% /
/dev/sdb1             7.3G  2.2G  4.8G  31% /home

```

Now I have 318MB of additional space on the internal drive and it only took me about 2 minutes to complete. How long would this take if you had to reinstall/reconfigure that amount of games/programs on a separate drive in Windows?

Caveat: The only thing with this method is you shouldn't name a user "opt" since creating a user with that name would fail since the owner of the directory is root. If you must have a user named "opt" you can solve this by making two partitions on the drive with one for /home and one for files.

---

### Post by adam814 on 2010-02-15
I'll add one more caution with moving files out to other partitions and making symlinks like that:

Don't do it with files in /bin, /sbin, or /lib.  Those programs/libraries are needed to boot the system (probably needed before your home partition would mount).  If you were to move them somewhere under /home it would cause problems.  Something as simple as a scheduled fsck could drop you to a busybox shell and you'd have to work around it to get it running.  Worse yet problems with your /home partition could force you to reinstall.

Files under /usr should be safe enough (in fact many Linux systems have a separate /usr partition anyway).

---

### Post by warp99 on 2010-02-15
> **adam814 said:**
> i'll add one more caution with moving files out to other partitions and making symlinks like that:

Don't do it with files in /bin, /sbin, or /lib ...

+1 8)

---

