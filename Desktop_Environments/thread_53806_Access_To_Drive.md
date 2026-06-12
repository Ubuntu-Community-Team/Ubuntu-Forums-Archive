---
title: "Access To Drive"
date: 2005-08-02
forum: Desktop Environments
---

### Post by alec on 2005-08-02
Hi

I have managed to re-format my USB external drive, using qtparted. I now find myself with one last (I hope) problem to solve before I can use this drive.

The drive is only giving access to root. 

Question: How do I change the access to me as user?



How much simpler things would be with a root account....

---

### Post by Zelut on 2005-08-02
I come up with two ideas off the top of my head.

One, you could try to 'chown' the drive.  (I've never tried it, but its worth a shot).  #sudo chown -R user:user /mount-point-of-drive.  That may change the ownership to you vs root.

Also, you can use the ubuntuguide.org to set a root password & use that when you need access to the drive...  hope that helps

---

### Post by heimo on 2005-08-02
Make a line like this to /etc/fstab:
 ```

/dev/sdc	    /media/sdc	  vfat    user,noauto	 0	   0

``` 

That should allow regular user to mount device /dev/sdc to mount point /media/sdc

---

### Post by Omnios on 2005-08-02
Not shure if this helped but its a thread of when I was trying to install wine on my document drive. There is the mount info for mounting as user and a few other mounting info in it that may help though.

[http://ubuntuforums.org/showthread.php?t=49830](http://ubuntuforums.org/showthread.php?t=49830)

---

### Post by alec on 2005-08-02
Had a frustrating but informative day getting this drive to work. In the end I had a cup of tea and then another look at the problem. I realised that I was being confused by the use of root as owner, when the problem was one of permissions.

I kdesu Konqueror and changed the permissions for others and group to read/write. Problem solved... 

Thanks for all the advice, and sorry for laying out the problem so badly.

---

