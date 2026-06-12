---
title: "X server cannot start"
date: 2008-06-27
forum: Desktop Environments
---

### Post by cheics on 2008-06-27
Just did a distro upgrade on by eeePC; and I had my battery die about a half hour later ;(

so I attempt to start up again and;
X server cannot start

I can get into a bash terminal though and I guess I could muck around a bit; but I'm not sure what direction to take

I have a live USB stick for eeeXubuntu; is there a way to boot up and fix the X server problem w/o reinstalling the OS?

---

### Post by Rocket2DMn on 2008-06-27
What error does it give you?  Can you login from the terminal and run either of these
```
startx
sudo /etc/init.d/gdm start
```
(may need to use xdm for that second command).

---

### Post by pytheas22 on 2008-06-27
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

might fix it, although looking at the error messages would be a cleaner approach.

---

### Post by cheics on 2008-06-27
#:startx
gives me:
----
mktemp: cannot create temp file /tmp/serverauth.wWidsg5314: Readd-only file system
/usr/bin/startx: line 139: cannot create temp file for here document: Read-only file system
xauth: error in locking authority file //.Xauthority
/usr/bin/startx: line 151: cannot create temp file for here document: Read-only file system
xauth: error in locking authority file //.Xauthority
/usr/bin/startx: line 151: cannot create temp file for here document: Read-only file system

Fatal server error:
Could not create lock file in /tmp.tx0-lock

giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (ernno 3): Server error.
xauth: error in locking authority file //.Xauthority
-----



#:sudo /etc/init.d/gdm start
gives me:
----
 * Starting GNOME Display Manager...   [OK]
----



#:sudo dpkg-reconfigure -phigh xserver-xorg
gives me:
----
/var/lib/dpkg/info/xserver-xorg.postinst: 1785: cannot create /var/lib/x11/X.roster: Read-only file system
----


So.... my preliminary diagnosis is 'read-only' file system
Not sure why it is suddenly read only; or how to switch it back

a ls -l on /var/lib/x11 reveals that all the files have -rw-r--r-- permisions

tried to change permissions with chmod, couldn't because of read only filesystem

So.. I leave it as an excersize to the reader to fix my problem ;)

---

### Post by Rocket2DMn on 2008-06-27
OK, reboot from the terminal with 
```
sudo shutdown -rF now
```
This will reboot the system and force it run fsck (a file system check).

---

### Post by cheics on 2008-06-28
no luck

I ran fsck, found no errors on any device

Is there a command to change a filesystem from read-only to r/w ?

---

### Post by cheics on 2008-06-28
figured it out...

saw some other post about a messed up fstab giving similar symptoms, and I'm fixed

Thanks for all the help!

---

