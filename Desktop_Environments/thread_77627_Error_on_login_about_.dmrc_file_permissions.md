---
title: "Error on login about .dmrc file permissions?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by ChrisTheGeek on 2005-10-17
Hi,

Everytime I log in to Gnome I get an error message saying that the ~/.dmrc file has the wrong permissions and that my session changes won't be persisted.

The really odd thing is that the error says the file must be owned by me and have 644 permissions - which it is and does!

Does anybody know what's causing this error or how to fix it? I haven't changed the permissions of any files since installing.

Many thanks.

---

### Post by Stephen-I-M on 2005-10-19
I'm getting the same thing. I don't know the problem either. My .dmrc is 644.

Stephen

---

### Post by migueljacq on 2005-10-19
The chmod 700 seems to have worked for some. view this thread

[http://ubuntuforums.org/showthread.php?t=72988](http://ubuntuforums.org/showthread.php?t=72988)

let me know how it goes

---

### Post by Bill Statler on 2005-10-19
Note that this is chmod 700 for your home directory, not for just the .dmrc file.

I don't like this because I want my home directory to be accessible to 2 other users.  I see that there are a couple of settings in the /etc/gdm/gdm.conf file that *ought* to affect this:

```
RelaxPermissions=0
```
The default value of 0 is supposed to mean that gdm will ignore everything except user-owned files and directories; 1 allows group write permissions; 2 allows all write permissions.

So far I've tried changing this to 1, and that didn't fix it.

There's also:
```
CheckDirOwner=true
```
which is supposed to control checking if directories are owned by the logon user.  I haven't played with this yet.

I'll do some more experiments and post if I find what works -- but if somebody can read (and understand) the gdm source code, maybe you can tell us exactly what the software wants.

---

### Post by ChrisTheGeek on 2005-10-20
Thanks very much for the reply.  chmod 700 worked fine on the home directory and I no longer get the message when I log on.

I'm curious how this error occurred though since I didn't mess with the permissions of ~ or ~/.dmrc.  It did happen after I'd added an additional user to the system but I'm not sure if this is just a co-incidence.

---

### Post by migueljacq on 2005-10-20
[QUOTE=ChrisTheGeek]Thanks very much for the reply.  chmod 700 worked fine on the home directory and I no longer get the message when I log on.

I'm curious how this error occurred though since I didn't mess with the permissions of ~ or ~/.dmrc.  It did happen after I'd added an additional user to the system but I'm not sure if this is just a co-incidence.[/QUOTE]

Someone offered a reason here:

[http://ubuntuforums.org/showpost.php?p=396235&postcount=9](http://ubuntuforums.org/showpost.php?p=396235&postcount=9)

So it's nothing you've done, it's just a little quirk of sorts apparently.

---

### Post by Bill Statler on 2005-10-23
Okay, here is the complete explanation (I think):

PROBLEM:  When you log in, several errors occur:

1: If you've enabled a greeter that displays user photos, the chosen login photo for one or more users is not displayed, and you just see a default image.

2: Immediately after login, you receive the following message on-screen:

> Your $HOME/.dmrc file has incorrect
permissions and is being ignored.
This prevents the default session
and language from being saved.
File sould be owned by user and have
644 permissions.

3: In /var/log/syslog, you find error messages something like these:

> ...
Oct 22 15:20:06 localhost gdm[4545]: run_pictures: /home/bill is writable by group.
Oct 22 15:20:06 localhost gdm[4545]: run_pictures: /home/lenna is writable by group.
...
Oct 22 15:20:54 localhost gdm[4545]: gdm_slave_session_start: /home/bill is writable by group.
Oct 22 15:20:59 localhost gdm[4545]: gdm_auth_user_add: /home/bill is writable by group.
...


EXPLANATION:  By default, GDM strongly dislikes files not owned by the user, and directories that can be written by anyone other than the user.  So if a user has changed the default permissions on his/her home directory, errors like this are likely.

The post-login message about the $HOME/.dmrc file is actually incomplete, and this has caused confusion for some people.  Not only does the file need to be owned by the user, with 644 permissions, but also the directory needs to be owned by the user, with 700 permissions.

This can be a real annoyance if, for some reason, you want your home directory to be writable by other users.


SOLUTION:  There are two keys in /etc/gdm/gdm.conf that affect whether GDM tolerates files and directories accessible by other users.  These can be changed by editing /etc/gdm/gdm.conf (note that you must use "sudo" or login as root to do this).  Look for the following section:

```
# 0 is the most restrictive, 1 allows group write permissions, 2 allows all
# write permissions
RelaxPermissions=0
# Check if directories are owned by logon user.  Set to false, if you have, for
# example, home directories owned by some other user.
CheckDirOwner=true
```

If you have syslog error messages like the ones shown above, try changing "RelaxPermissions=0" to "RelaxPermissions=1": this will tell GDM it's OK to use the directory even though other users of the same group can write to it.  If your home directory is writable by everybody, you'll need to make that "RelaxPermissions=2".

If you don't own your home directory, change "CheckDirOwner=true" to "CheckDirOwner=false".

After editing and saving /etc/gdm/gdm.conf, YOU MUST RESTART YOUR COMPUTER in order for the changes to take effect.  It is not enough to just logout/login, or even to restart GDM, because these particular keys are read from the config file only once, the first time that GDM starts up.  (I won't tell you how much time I wasted before I figured that out!)

Good luck!

---

### Post by mwinther on 2005-11-02
I've had the same problem as stated above, but changing the permissions of .bashrc and ~ didn't work for me, and neither did changing gdm.conf  :( 

After doing a little research i saw that the owner of my homedir was root, which seemed a little wrong to me..

I figured that all i had to do was to change the group and owner-permissions, and thankfully it worked :)

What i did:
```

sudo chown myusername /home/myusername
sudo chgrp myusername /home/myusername

```

---

### Post by thephotoman on 2006-10-19
Thanks for this tip.  I've been trying to figure the problem out for myself for some time now.

---

