---
title: "Can't move /home dir"
date: 2009-02-21
forum: General Help
---

### Post by davidself1001 on 2009-02-21
I am trying to move my /home dir to a new disk.  When I try to either mv the /home to /home.bak or umount the /home dir I get the following error.

sudo mv /home /home.bak
mv: cannot move `/home' to `/home.bak': Device or resource busy
/$ sudo umount /dev/sda1
umount: /home: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

My plan is to use the following recommended procedure but I can't get past the first step:

mv /home /home.bak
mkdir /home
mount -t ext3 /dev/sda3 /home
cp -a /home.bak/* /home

---

### Post by davidself1001 on 2009-02-21
A little more detail.  I currently have my /home dir in a 160G drive and want to move it to a /1TB drive.  I copied the contents of the 160G drive to the other drive and tried to just change the mount instructions in /etc/fstab from the old to new disk but it didn't work.  I get some /HOME isn't recognized or some such error when logging in.  One thing I noticed was that if I go into a failsave terminal and type cd ~, followed by ls it shows Desktop as the only thing in dir.  If I do cd /home and do an ls I get my name as a subdir.  Don't know if that helps but...

---

### Post by cariboo on 2009-02-21
The way I would do it is to copy your home directory to the new drive, then restart in recovery mode and edit fstab using nano to have /home point to the new drive eg:

Change:

```
/dev/sda2  /home  ext3   relatime  0  2
```

to

```
/dev/sdb1 /home    ext3   relatime  0  2
```

susbstitute your device labels for the ones in the example.

Jim

---

### Post by wirelessmonkey on 2009-02-21
First you need to get out of your home directory...
```
 cd /var (or anywhere that's not on sda1)
sudo mv /home /home.bak
```

Give that a try, and let us know what happens!

---

### Post by davidself1001 on 2009-02-21
Getting out of the /home dir didn't make any difference.  Still get the busy error.  Also, I had tried copying my home content to the new disk and redirected /home to that disk and that's when I get the HOME dir error as described above.  I am not using the relatime option I have it set as follows:

/dev/sdb1 /home ext3 defaults,errors=remount-ro 0 1

---

### Post by FrostDust on 2009-02-21
You can't move or unmount a directory when you're using it. Because any user account uses /home, you'd have to either:

1) When your computer starts, try logging in with "Recovery Mode" and try your plan from there. You log in as root when you do this, which uses /root/home, instead of /home.
2) Boot up using a live CD (the Ubuntu install disc should work), as these don't use or mount /home unless you explicitly tell it to.

When you've successfully moved /home, do what cariboo907 said, before you reboot into your normal user account, and edit /etc/fstab to reflect the change.

---

### Post by davidself1001 on 2009-02-21
Thanks for all the help.  I figured out that when I copied over my /home files to the new disk I had done it with the /root Nautilus package and it did not have the "view hidden files" set (which i have as default in the standard Nautilus).  So the net result was that I was missing all of the .xxx files and that was causing the problem.

---

### Post by lensman3 on 2009-02-21
Try this.  Copy the entire directory to the new disk.  Use "cp -Rpv <source> <target>".  Then rename the old home to something else.  THEN set up a soft link ->  ln -s <new-disk-location> /home/old-location.

You have to move the old location to the new location.  Then point using the new location using the "ln -s" command.   Then reboot (though logging completely  out and back-in might work) because you have to get the Kernel and login scripts pointing to the new location.  Then if you really want it to move you will have to change the home directory field in the /etc/passwd file.  

Same rules apply to /home.  You have to copy it all to a new location. Rename the old. Point /etc/passwd to  the new location. Finally mounting the new location under the new mount-point.

The above is easier if you do it from a command line as root and in single user boot mode.  That way you can make the old files read-only and the files don't change during the copy.  There are options with the mount command to force a file system as read-only.  

Recall that to test if everything is working to use the "su <user>" where <user> is the login ID of the files being moved.  When you "su" (pronouced ESS-YOU) the command forces the user to become a user.  su by itself defaults to root, su with a login ID becomes that user.

---

### Post by handy on 2009-02-21
The following how-to may hopefully throw some light on the problem:

*_[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)_*

---

