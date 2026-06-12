---
title: "Problems with sound"
date: 2005-12-01
forum: Desktop Environments
---

### Post by bbellantuono on 2005-12-01
Hi All,
I've just installed Ubuntu 5.10 on my machine, and apparently it detected all my hardware. Everything works perfectly with my user (including sound).

But when adding a new user, loging in with it, sound doesn't work for the user. Even the volume control is not enabled for the user.

First user (that works) has uid/gid=1000 and the second user (that does not work) has uid/gid=1001.

Does anybody know what's happening?

Tks,
Bruno

---

### Post by Sutekh on 2005-12-01
Perhaps your second user isn't in the audio group, which would allow it use of audio stuff.  This often happens when new users are created; they don't have all the privileges as the first user

Two ways to check;
First Way; 
Type at a terminal command line
```

groups <secondusername>

```
This will list the groups that your second user belongs to.

Here's my output for my first user
```

user@ubuntu:~$ groups user
user : user adm dialout cdrom floppy **audio** dip video plugdev lpadmin scanner admin multimedia
user@ubuntu:~$

```
Notice it belongs to the group audio.

To add your new user to the audio group
```

sudo adduser <secondusername> **audio**

```
Then the new user will be able to use audio devices, change volume etc.

Second way, GUI;
Go to System -> Administration -> Users and Groups
you will need to enter your sudo password.  
Find your new user and select properties.  
In properties go to the user privileges tab and check the line "Use audio devices"

That should set you up.  Note the same may be needed to use the CD-ROM, removable media, ...

---

