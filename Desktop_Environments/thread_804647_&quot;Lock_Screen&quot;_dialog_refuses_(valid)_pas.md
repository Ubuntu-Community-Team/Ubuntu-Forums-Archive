---
title: "&quot;Lock Screen&quot; dialog refuses (valid) password."
date: 2008-05-23
forum: Desktop Environments
---

### Post by dsm iv tr on 2008-05-23
Hey!

Hoping someone might have the same issue.

Essentially, gdm's "Lock Screen" dialog refuses my login password after the screen in locked, either after a resume/hibernate, or simply telling it to lock the screen without any power management.

I've tried changing my password with passwd, rebooting, and altering my login keyring to have the same password as my UNIX login.

I'm going to disable screen locking for now, but does anyone have any ideas? It's driving me crazy.

Edit: Additional info, I just did an apt-get update run today, and it updated gnutls and some ssl libs. If you need logs, lemme know. I -can- login just fine from an initial GDM login screen.
Edit #2: I forgot to mention that locking the screen worked perfectly fine before the apt-get update.

---

### Post by sdennie on 2008-05-23
Are you using multiple keyboard layouts?  Is it possible that your password generates different keys in those layouts?  Another possibility could be the state of the numlock key on resume.  Some laptops map the right hand side of the keyboard to the numberpad when numlock is on (and it's incredibly confusing if you don't realize what's going on).

---

### Post by dsm iv tr on 2008-05-23
I'm not using multiple k/b layouts. I do use my compose key (for French accents), but there's no numlock or capslock of any kind turned on. I'm pretty much stumped.

I've run across one other mention of this on a Google search, but no real solutions.

Is there a way to "reset" gdm? Would purging the package and reinstalling from apt possibly fix this in any way? I'm a longtime Debian user, not used to reinstalling stuff unless I really have to, but I'd be willing to make an exception. :)

/var/log/auth also spits out a bunch of "unknown user" and "authentication failed" every time the dialog refuses me access. I haven't changed my uid or username.

---

### Post by dsm iv tr on 2008-05-24
Bump.

---

### Post by fritserasmus on 2008-09-03
I am experiencing the same issue.

When "Lock Screen" is clicked I cannot log onto the pc again using the gui interface.

I tried my uid with admin rights pw, in any shape or form but was not successful.

Had to hard reset the pc so I can restart Ubuntu.

The PC / file server now runs with no gui interface protection. 
Any suggestions?

Rgds

Frits

---

### Post by dsm iv tr on 2008-09-03
I still haven't found a solution. I checked the PAM config and that's fine too. I'm pretty much lost on it. :\

---

### Post by iLoveRuby on 2008-09-04
I'm having the same problem.  When I "Lock Screen", log back in, I have to "Switch User" and type in the user name then password.  I've tried recreating user, reenabling administrative privileges, etc...

---

### Post by Veloso on 2008-09-25
Bumping the thread; I'm having the same problem myself.

---

### Post by dsm iv tr on 2008-09-29
I'm still experiencing this issue, months later.

Maybe it's time for a Launchpad bug.

---

### Post by Rhubarb on 2008-10-08
It's a known bug, see here:
[https://answers.launchpad.net/ubuntu-eee/+question/45385](https://answers.launchpad.net/ubuntu-eee/+question/45385)

Salgar has the solution:
> CAUSE:
/sbin/unix_chkpwd has wrong group/permissions

SOLUTION:
chown root:shadow /sbin/unix_chkpwd
chmod 2755 /sbin/unix_chkpwd

---

### Post by iLoveRuby on 2008-10-11
You may also need to change the group permission of /etc/shadow

> have a look at the files /etc/shadow and /sbin/unix_chkpwd. The owner
should be "root" for the user, and "shadow" for the group. 

(See: [http://groups.google.com/group/linux.debian.user/browse_thread/thread/4f487ced7818487c]("http://groups.google.com/group/linux.debian.user/browse_thread/thread/4f487ced7818487c"))

So, the revised solution would perhaps be:

```
CAUSE:
/sbin/unix_chkpwd and /etc/shadow have wrong group/permissions

SOLUTION:
chown root:shadow /sbin/unix_chkpwd
chmod 2755 /sbin/unix_chkpwd
chown root:shadow /etc/shadow
```

---

### Post by iLoveRuby on 2008-10-29
**Update**: This problem was fixed in Ubuntu 8.10.

---

### Post by iamhugeinjapan on 2008-11-02
I've just started getting it in Ubuntu 8.10 (fresh install but old /home). It will intermittently require two password attempts to gain access. I've very carefully typed my password to test this and it will be denied. I tried changing my password but it continues.

---

### Post by fatka on 2009-01-19
I have this problem on two different installs of Hardy (one is Xubuntu the other is regular Gnome). In my machine the ownership and permissions are already set as mentioned in the solution. Any fixes?

---

### Post by iamhugeinjapan on 2009-01-19
I solved it by upgrading to Intrepid :)

Come on up, the water is nice.

---

### Post by fatka on 2009-01-20
I can't upgrade as some of the packages I need to work with are not very stable on Intrepid. :(

---

### Post by mattfink on 2009-02-10
> **Rhubarb said:**
> It's a known bug, see here:
[https://answers.launchpad.net/ubuntu-eee/+question/45385](https://answers.launchpad.net/ubuntu-eee/+question/45385)

Salgar has the solution:

 ```

CAUSE:
/sbin/unix_chkpwd has wrong group/permissions

SOLUTION:
sudo chown root:shadow /sbin/unix_chkpwd
sudo chmod 2755 /sbin/unix_chkpwd 
```



This worked for me on Ubuntu EEE (8.04)

---

### Post by rstrazza on 2009-04-02
I have installed version 8.10 will all updates and default Gnome 2.24.1 and after try the proposed solutions on this thread the lock screen still refuses my valid password. Any other ideas ?

Thanks

---

### Post by Futurix on 2009-09-06
use this :
chown root:shadow /sbin/unix_chkpwd
chmod +s /usr/lib/gnome-screensaver/gnome-screensaver-dialog
chmod +s /sbin/unix_chkpwd
chown root:shadow /etc/shadow

for kde users:
chmod +s /usr/bin/kcheckpass

tested on ubuntu 9.04

---

### Post by Rogerborg on 2009-09-15
Yup, this bug is still extant in 9.04.  The stock install was fine, but somewhere along the way, my /etc/shadow has become root:root and 0400.

I'm not sure what's causing it.  Running useradd sets the permissions to 0440, but doesn't touch the permissions.

sudo chown root:shadow /etc/shadow
sudo chmod 440 /etc/shadow

fixes the screen unlock problem for me in 9.04.

---

### Post by paschadee on 2010-02-15
Occurred on Ubuntu 9.10 (after restoring some files from an rsync backup - reason unknown - affected files not included in backup/restore)

before fix:

paul@godzilla:~$ ls -l /dev/null
-rw-rw-rw- 1 root root 51 2010-02-15 10:53 /dev/null
paul@godzilla:~$ su
Password: 
root@godzilla:/home/paul# rm -rf /dev/null; mknod -m 666 /dev/null c 1 3
root@godzilla:/home/paul# ls -l /dev/null
crw-rw-rw- 1 root root 1, 3 2010-02-15 10:54 /dev/null
root@godzilla:/home/paul# ls -l /sbin/unix_chkpwd 
-rwxr-sr-x 1 root shadow 30400 2009-09-04 10:26 /sbin/unix_chkpwd
root@godzilla:/home/paul# chmod +x /sbin/unix_chkpwd 
root@godzilla:/home/paul# chmod +s /sbin/unix_chkpwd 
root@godzilla:/home/paul# ls -l /sbin/unix_chkpwd 
-rwsr-sr-x 1 root shadow 30400 2009-09-04 10:26 /sbin/unix_chkpwd
root@godzilla:/home/paul# 


GDM screensaver login success.

---

### Post by venturax on 2010-03-03
> **fatka said:**
> I have this problem on two different installs of Hardy (one is Xubuntu the other is regular Gnome). In my machine the ownership and permissions are already set as mentioned in the solution. Any fixes?

I'm running Karmic and as fatka mentions, the ownership and permissions look ok. Still i get locked out. I can circumvent the issue by clicking "Switch User" and log in as mysefl again...

---

### Post by jazzgossen on 2010-11-05
I have this problem on Ubuntu 10.04. Logging on works in all cases except from a locked screen. The ownerships and permissions look OK. I did 
chmod +s /sbin/unix_chkpwd
but the problem is still the same.

---

