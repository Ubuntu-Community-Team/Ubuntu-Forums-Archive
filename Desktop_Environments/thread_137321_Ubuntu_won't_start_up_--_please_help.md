---
title: "Ubuntu won't start up -- please help"
date: 2006-02-27
forum: Desktop Environments
---

### Post by KevNice on 2006-02-27
Hi again,

OK, everything was starting to finally work properly and I was getting used to Ubuntu.. then for some reason LimeWire wasn't opening, so I rebooted the computer. Upon rebooting and trying to log in, I get this something about my session only lasting 10 seconds and a failure. The message also had these lines of code--

[/etc/gdm/PreSession/Default: Registering your system with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -
/etc/gdm/Xsession: beginning session setup...
mkdtemp: private socket dir: Permission denied.]

So it recommends that I load Ubuntu in failsafe GNOME mode. I try it and I get this subsequent message-- 

[Could not open or create the file "(null)". This indicates that there may be a problem in your configuration. The error was "Failed to create file '/tmp/gconf-test-locking-file-zafujp': Permission denied" (errno=2)]

I can still get in with Failsafe terminal though.

It keeps referring to the temp folder, so my only guess is that it has something to do with the ClamAV 0.88 update that I was instructed to depackage to that folder. Go figure, an anti virus program causing my system to crash...

Any ideas?

---

### Post by zxee on 2006-02-27
I don't use limewire so I have no idea about that part of it, but I have recovered from permissions problems that won't let you log in, and that seems like what you have. To fix a "session only lasted less than 10 seconds" error I have done this (you can google that error also) 
From terminal/commandline 'cd /home'
'sudo chmod 700 yourusername' 
'sudo chown username username'
'chgrp username username'
'cd username'
'sudo chmod -R 777*'   
Of course the "username" is your specific user-good luck.

---

### Post by KevNice on 2006-02-27
thanks for the help.. but the last line of those commands "sudo chmod -R 777*" didnt work, said that there were too few arguments. If I wasnt such a Linux beginner maybe I could figure it out, but I couldnt..

---

### Post by KevNice on 2006-02-28
by the way, I tried the .ICEauthority delete method. There was an .ICEauthority file, but deleting it didn't fix the problem..

---

### Post by bernardfrancois on 2006-02-28
I have the same error when I try to log on to ubuntu.
At first, my disk was full, causing me not to be able to log on to gnome.
After removing some of my files, I could log in again.
Later, my disk was full again, so I decided to uninstall Oracle (a 3,6Gb database program) manually and delete the oracle user and user's directory (using *sudo userdel oracle* and *sudo rm -rf /home/oracle*) I still wasn't able to log on to gnome.

Here is some console output:
```

ber@ubuntu:~$ cat .xsession-errors 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ber"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied
ber@ubuntu:~$ man date
man: can't create a temporary filename: Permission denied
ber@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             5.7G  1.9G  3.6G  34% /
tmpfs                 158M     0  158M   0% /dev/shm
/dev                  5.7G  1.9G  3.6G  34% /.dev
none                  5.0M  2.8M  2.3M  55% /dev
ber@ubuntu:~$ echo "this is a test to see if I can make a file" > newfile
ber@ubuntu:~$ ls -l newfile
-rw-r--r--  1 ber ber 43 2006-02-28 12:49 newfile
ber@ubuntu:~$ sudo df -h
Password:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             5.7G  1.9G  3.6G  34% /
tmpfs                 158M     0  158M   0% /dev/shm
/dev                  5.7G  1.9G  3.6G  34% /.dev
none                  5.0M  2.8M  2.3M  55% /dev
ber@ubuntu:~$ rgrep -v '^#.*$' /etc/security/limits.conf 



soft nproc 2407
hard nproc 16384
soft nofile 1024
hard nofile 65536
ber@ubuntu:~$ sudo man date
Reformatting date(1), please wait...

ber@ubuntu:~$ mktemp
mktemp: cannot create temp file /tmp/tmp.HYKPzF: Permission denied

ber@ubuntu:~$ sudo mktemp
Password:

/tmp/tmp.N6IMAJ
ber@ubuntu:~$ grep ber /etc/passwd
ber:x:1000:1000:ber,,,:/home/ber:/bin/bash
ber@ubuntu:~$ ls -ld /tmp
drwxr-xr-x  4 root root 4096 2006-02-28 13:12 /tmp

```

As you can see, my user can't make any files in /tmp and can't open manual pages, while the user root can do this.
The problem is not the limits, since my user (ber) can actually see the 3.6G available disk space.
I don't think the permission of my /tmp folder changed; and besides there are also acces problems to other folders...

---

### Post by bernardfrancois on 2006-02-28
**sudo chmod 1777 /tmp** solved it. I dunno how come those permissions changed...

---

### Post by KevNice on 2006-02-28
Thanks Bernard. That did it for me too! Strange..

---

### Post by zxee on 2006-02-28
The best thing is you figured it out-good going! The command I provided works with slackware ( i multiboot several distros ) but obviously doesn't work in debian based linux. I'm making a note of that command. I'm sure you helped others too.

---

### Post by bernardfrancois on 2006-02-28
Well, then here's a little more information so you can understand what the command exactly does:

chmod can change the permissons on a file or directory.
1777 is the octal representation of drwxrwxrwt
/tmp is the directory on which we apply the changes

about the octal representation:

1 : sticky bit on - this makes sure that only the owner of a file can remove it, instead of the owner of the directory (which is the default)
This is necessary for the /tmp directory, where all users are allowed to store their temporary files. Offcourse those files shouldn't be deleted by any other user.

7: means that the read,write and execute bits are set (the octal representation of binary 111 is 7) for a specific user group

the first 7 is for the owner of the file, the 2nd is for the members of the group-owner of the file, and the last one is for the 'world' (meaning all users)

For more info you can read **man chmod**, and for even more info **info chmod**.

---

