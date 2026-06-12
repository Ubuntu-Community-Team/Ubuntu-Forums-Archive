---
title: "/ partition space problems"
date: 2005-12-11
forum: General Help
---

### Post by zoqaeski on 2005-12-11
When I did the upgrade from 5.04 to 5.10, it crashed because it ran out of space on my / partition to store the packages as they were downloaded. Is there a way to relocate the place where they are stored, maybe symlinking from another drive perhaps?

EDIT: It turns out that I was too dumb to set up a /var partition from the outset; all I've got are /, /boot, /opt, /home and /usr. Should I edit the /etc/fstab and change /opt to  /var (I've got a couple of GiB there that don't get used, and this might prevent a crash like last time). Changing the mount point of a partition doesn't affect things too much, does it?

cheers
Robbie

---

### Post by Oldan on 2005-12-11
[QUOTE=zoqaeski]all I've got are /, /boot, /opt, /home and /usr. Should I edit the /etc/fstab and change /opt to  /var (I've got a couple of GiB there that don't get used, and this might prevent a crash like last time). Changing the mount point of a partition doesn't affect things too much, does it?[/QUOTE]

It all depends on what you've got there!
You actually have a */var* partition, it's part of /. Which may be why you ran out of space on root. If you want to move your /var to another physical partition, you have to copy the files already there to the new partition and then mount it over the top of the existing directory (which now becomes a "mount point". You can't just change the mount point for /opt. Your current install won't be able to find things like /var/log (for logs) and /var/cache (which is where I'm betting the problem is) and /var/run (for daemons).

--Oldan

---

### Post by zoqaeski on 2005-12-12
I've stuffed up big time now - I moved the var to a new location called /var2; worst bit is I can't undo it cos nothing can be found!
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by steevc on 2005-12-15
I have a similar problem in that my 5GB / partition has filled up. I recently cleared about 400MB there but doing an apt-get clean and uninstalling some software.

I think it got filled when I tried to back up using konserve and it created the tar file in /tmp/<something> (can't remember exactly).

I have other partitions for /home and /data. What do I need to do to move some of the larger folders on / to one of those? Is it just a matter of coping the directory and creating a link?

I would probably want to move those directories that contain temporary data that is not part of the core system.

---

### Post by Oldan on 2005-12-20
[QUOTE=steevc]I think it got filled when I tried to back up using konserve and it created the tar file in /tmp/<something> (can't remember exactly).[/QUOTE]

bootclean.sh is designed to clean out everything in your /tmp directory at boot time (unless TMPTIME < 0 or "infinite"). You should not count on things in /tmp /var/run or /var/lock being there next time you reboot!

[QUOTE=steevc]I have other partitions for /home and /data. What do I need to do to move some of the larger folders on / to one of those? Is it just a matter of coping the directory and creating a link?[/QUOTE]

You can remount portions of your disk in /home or /data, but you are running a risk of creating convoluted mount points and intricate fstab settings.

As you suggest, putting a symbolic link might be a better choice - but certainly not for the long term. Keeping /var and /tmp in separate partitions is the best idea, but for that, you'd need to repartition your drive.

You can also add another drive and move all the data in /var to a partition on it and then mount it on top of the /var directory. Ditto with /tmp.

--Oldan

---

### Post by Oldan on 2005-12-20
[QUOTE=zoqaeski]I've stuffed up big time now - I moved the var to a new location called /var2; worst bit is I can't undo it cos nothing can be found![/QUOTE]

Hmmmmm... you might want to boot with a live cd and modify your fstab. That way you can at least get back into business.

And don't ask me how I know that will work! :oops: 
--Oldan

---

