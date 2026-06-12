---
title: "Sharing Local Folders - Why difficult?"
date: 2009-05-04
forum: General Help
---

### Post by randyklein99 on 2009-05-04
All I want to do is have a folder (family photos) that 2 users (me and my wife) can add, edit, and delete files in.  

So far, I have created a new folder called /home/Pictures and created a group called 'adults' and added my wife and myself. Then I've tried doing the permissions thing (giving the group adults the rwx permissions), but that doesn't seem to inherit to new files--I get permission denied when I try to paste new files there.  Am I doing something wrong?

Samba seems a popular answer, but that seems more geared towards sharing across a network and not just between 2 users on the same machine.  Is Samba still the answer in this case?

And I've started reading about ACL, but theres conflicting stuff on that and most threads about it are old. 

Any help would be greatly appreciated.

---

### Post by taurus on 2009-05-04
What's the output of this command from a terminal?

```
ls -la /home/Pictures
```

---

### Post by randyklein99 on 2009-05-04
```

drwxrwxrwx 2 root adults 4096 2009-05-04 19:11 .
drwxr-xr-x 9 root root   4096 2009-05-04 19:11 ..

```

---

### Post by taurus on 2009-05-04
```
ls -la /home
```

---

### Post by randyklein99 on 2009-05-04
```

total 48
drwxr-xr-x  9 root  root    4096 2009-05-04 19:11 .
drwxr-xr-x 22 root  root    4096 2009-05-03 07:35 ..
drwxr-xr-x 32 amy   amy     4096 2009-05-04 20:28 amy
drwxr-xr-x 30 kody  kody    4096 2009-04-27 17:59 kody
drwx------  2 root  root   16384 2009-04-24 06:43 lost+found
drwxrwxr--  2 root  adults  4096 2009-05-04 21:26 Pictures
drwxr-xr-x 56 randy randy   4096 2009-05-04 20:58 randy
drwxr-xr-x  3 root  root    4096 2009-04-26 09:08 remastersys
drwxr-xr-x  2 kody  kody    4096 2009-04-24 07:13 temp

```

---

### Post by taurus on 2009-05-04
Any error message when you run those commands from a terminal?

```
sudo chmod -R 770 /home/Pictures
touch /home/Pictures/test
ls -la /home/Pictures
```

---

### Post by randyklein99 on 2009-05-04
No errors this time.  But last time I did the touch test, there were permission errors.  Do you have to relogin after creating a group and/or changing permissions?  Because I have relogged and I think that's why the touch test did not give me errors.

But as this output shows, I don't think the group permissions were inherited for the test file.

```

total 8
drwxrwx--- 2 root  adults 4096 2009-05-04 21:26 .
drwxr-xr-x 9 root  root   4096 2009-05-04 19:11 ..
-rwxrwx--- 1 randy randy     0 2009-05-04 21:30 test

```

edit: wait, I do think the permissions were inherited, did that fix it?

---

### Post by taurus on 2009-05-04
Yes, you need to log out and back in again when you change groups.  Why not make group adults as the primary group for you and your wife?

---

### Post by randyklein99 on 2009-05-04
Primary groups? what's that and how do you do it?

---

### Post by p0rkjello on 2009-05-04
You need to set the sgid bit on the directory.

Fix the rights..
```
chgrp -R adults /home/Pictures
```
Set the SGID
```
chmod g+s /home/Pictures
```

All files put into this directory will be owned by the "adult" group.

---

### Post by randyklein99 on 2009-05-04
That worked wonderfully. I guess it wasn't all that difficult if I had just re-logged.

Thank you for your assistance.

---

### Post by taurus on 2009-05-04
Look in /etc/group to see what GID is for adults.  Then, edit /etc/passwd and change the second value (for the first user, it's 1000:**[COLOR="Red"]1000[/COLOR]** in /etc/passwd) to the GID of adults.  Do the same thing for your wife.  If she is the second user that you created, then your UID and GID is the same then, 1001:**[COLOR="Red"]1001[/COLOR]**.

```
cat /etc/group
gksudo gedit /etc/passwd
```

Reboot and see of the changes stick.

```
id
```

---

### Post by randyklein99 on 2009-05-04
Is this last bit of code to make the chgrp and chmod changes stick? Or the primary gorup thing?

---

### Post by unutbu on 2009-05-04
Edit: Oops, sorry -- I didn't see p0rkjello and taurus's last posts.

If you do what taurus suggests, none of the stuff below is necessary.
-------------------------------------------------------

Run
```

chmod +s /home/Pictures
```

This sets the set-group-ID bit on the /home/Pictures directory.
Henceforth, all files and directories created inside the /home/Pictures directory will inheret the group ("adult") from /home/Pictures.

Note that if you make a directory in /home/Pictures, say, /home/Pictures/subdir
and then put files inside /home/Pictures/subdir, then these files will *not* have the "adult" group set because /home/Pictures/subdir does not have the set-group-ID bit set.

If you plan on making subdirectories, then one possible solution is to use dirmon: [http://ubuntuforums.org/showthread.php?t=1104716](http://ubuntuforums.org/showthread.php?t=1104716)

---

### Post by p0rkjello on 2009-05-04
> **unutbu said:**
> Edit: Oops, sorry -- I didn't see p0rkjello and taurus's last posts.

-------------------------------------------------------

Run
```

chmod +s /home/Pictures
```

This sets the set-group-ID bit on the /home/Pictures directory.
Henceforth, all files and directories created inside the /home/Pictures directory will inheret the group ("adult") from /home/Pictures.

Note that if you make a directory in /home/Pictures, say, /home/Pictures/subdir
and then put files inside /home/Pictures/subdir, then these files will *not* have the "adult" group sit because /home/Pictures/subdir does not have the set-group-ID bit set.

If you plan on making subdirectories, then one possible solution is to use dirmon: [http://ubuntuforums.org/showthread.php?t=1104716](http://ubuntuforums.org/showthread.php?t=1104716)

If you create a new directory inside of a directory with the SUID set it will also have the SUID bit set.

Only time that a new file will not have the SUID bit set is if it is moved (mv) into a SUID set directory..

---

### Post by unutbu on 2009-05-04
Indeed, you are correct. Thanks.

Another possible way to spoil the set-gid bit is to recursive copy a folder into /home/Pictures.

```
cp -a /source /home/Pictures 
```

or
```

rsync -a /source/ /home/Pictures/source/
```

---

