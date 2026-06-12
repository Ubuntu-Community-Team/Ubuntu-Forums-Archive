---
title: "[SOLVED] External Hard Drive Permissions"
date: 2009-01-03
forum: General Help
---

### Post by Captain_Jack on 2009-01-03
I have searched through several threads regarding changing permissions, and mounting external hard drives but I have not been able to make much sense of it being a first time Linux user.

My problem is this:

I decided to reformat an external hard drive that I use for data storage to a more linux friendly file system, as it had been formatted in NTFS previously.

I used Gparted to reformat the drive to ext3 and everything was successful. On remounting the drive, I was unable to add or change any files on the hard drive due to lack of permissions. Under the permissions tab it displays "The permissions of EXTERNAL could not be determined."

I would, obviously, like to change the permissions of the drive so that I can access it, and have it auto mount correctly. I have read a little on chown and such...but I am very new to terminal.

If anyone can help, it would be much appreciated!

---

### Post by taurus on 2009-01-03
What is the mount point of that external harddrive?

```
df -h
```
You need to change the ownership of that mount point from root to your login name if you want to write to it without using sudo/gksudo.

_Assuming_ the mount point for that external drive is /media/disk and your login name is jack, you could do something like

```
sudo chown -R jack:jack /media/disk
ls -la /media
```

---

### Post by Captain_Jack on 2009-01-03
The mount point is /media/EXTERNAL and I ran the sudo chown bit you suggested...after doing so it displayed:

jordan@juturna:~$ sudo chown -R jordan:jordan /media/EXTERNAL
[sudo] password for jordan: 
jordan@juturna:~$ ls -la /media
total 20
drwxr-xr-x  4 root   root   4096 2009-01-03 22:06 .
drwxr-xr-x 20 root   root   4096 2009-01-01 22:16 ..
lrwxrwxrwx  1 root   root      6 2009-01-01 17:01 cdrom -> cdrom0
drwxr-xr-x  2 root   root   4096 2009-01-01 17:01 cdrom0
drwxr-xr-x  3 jordan jordan 4096 2009-01-04 02:57 EXTERNAL
-rw-r--r--  1 root   root     63 2009-01-03 22:06 .hal-mtab
-rw-------  1 root   root      0 2009-01-03 22:06 .hal-mtab-lock

I attempted to write a file to disk afterward but it still does not allow it.

---

### Post by taurus on 2009-01-03
What happens when you run this command?

```
touch /media/EXTERNAL/testing
```

---

### Post by Captain_Jack on 2009-01-03
Well when I type it exactly as you wrote nothing happens, it just prompts for the next command. Forgetting the "/" before media results in:

jordan@juturna:~$ touch media/EXTERNAL/testing
touch: cannot touch `media/EXTERNAL/testing': No such file or directory
jordan@juturna:~$ 

Sorry I have no idea what any of these commands, or most of this information means.

---

### Post by taurus on 2009-01-04
What's the output of this one now?

```
ls -la /media/EXTERNAL
```

---

### Post by Captain_Jack on 2009-01-04
jordan@juturna:~$ ls -la /media/EXTERNAL
total 56
drwxr-xr-x 3 jordan jordan  4096 2009-01-03 22:56 .
drwxr-xr-x 4 root   root    4096 2009-01-03 22:53 ..
drwxr-xr-x 2 jordan jordan 49152 2009-01-04 02:57 lost+found
-rw-r--r-- 1 jordan jordan     0 2009-01-03 22:59 testing

There is also now a "Testing" file listed in the drive. I'm assuming that was part of the command I did previously?

---

### Post by taurus on 2009-01-04
> **Captain_Jack said:**
> jordan@juturna:~$ ls -la /media/EXTERNAL
total 56
drwxr-xr-x 3 jordan jordan  4096 2009-01-03 22:56 .
drwxr-xr-x 4 root   root    4096 2009-01-03 22:53 ..
drwxr-xr-x 2 jordan jordan 49152 2009-01-04 02:57 lost+found
**[COLOR="Blue"]-rw-r--r-- 1 jordan jordan     0 2009-01-03 22:59 testing[/COLOR]**

There is also now a "Testing" file listed in the drive. I'm assuming that was part of the command I did previously?

Yip.  The touch command created a file with 0 byte to it.  In this case, we called it testing.  So, you are able to write to /media/EXTERNAL.

If you want to remove it, run

```
rm /media/EXTERNAL/testing
ls -la /media/EXTERNAL
```

p.s.  By the way, Unix/Linux is case sensitive so testing is not the same as Testing.

---

### Post by Captain_Jack on 2009-01-04
Ah, I see. Now, this enables me to have write access through the command line? Can I have full read write access through the GUI? 

A quick try shows I can navigate into the drive and manually right-click delete both the testing file and the only folder on the drive. But I cannot Copy and Paste files into the drive this way. Or create new folders.

---

### Post by taurus on 2009-01-04
Are you using nautilus?  Remember, you have to restart nautilus.

```
mkdir /media/EXTERNAL/test
```
That should create a test directory in /media/EXTERNAL.

---

### Post by mc4man on 2009-01-04
I've always (perhaps unnecessarily), made a dir., mounted the /dev/sdxx to it, then chowned, unmounted, and let it remount as normal.

Ex.

```
mkdir /media/fix 
```

> 
doug@doug-desktop:~$ sudo mount /dev/sdb7 /media/fix
[sudo] password for doug: 
doug@doug-desktop:~$ sudo chown -R doug:doug /media/fix
doug@doug-desktop:~$ sudo umount /dev/sdb7


---

### Post by Captain_Jack on 2009-01-04
I used the command and voila, it created a new directory. So I assume things are working correctly now.

EXcuse my ignorance...but I do not know what nautilus is. Is that the interface for Ubuntu? Similar to explorer in Windows?

I have been a Windows user my entire life until about 2 weeks ago...so my knowledge is very limited.

---

### Post by taurus on 2009-01-04
How did you navigate to /media/EXTERNAL from GUI?

---

### Post by Captain_Jack on 2009-01-04
'Places' tab, to 'Home Folder' to EXTERNAL. I feel this is some sort of trick question. Ha, ha.

---

### Post by taurus on 2009-01-04
And you can't create directory or copy files to /media/EXTERNAL?

---

### Post by Captain_Jack on 2009-01-04
No, sorry. I never clarified afterward. I restarted after you said Nautilus needed to be restarted. Things now work fine. Full read / write access and the disk mounts correctly. Problem solved!

I was just asking what Nautilus was...because I did not know.

and thank you very much for the help, btw. I doubt I could have fixed this otherwise.

---

