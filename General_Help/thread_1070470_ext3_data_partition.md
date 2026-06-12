---
title: "ext3 data partition"
date: 2009-02-15
forum: General Help
---

### Post by Andreas1 on 2009-02-15
ok, i recently tossed ntfs and created a ext3 "data" partition for my personal files (i know i can make a /home partition but that is not what i want)

i tried the following in fstab, according to [http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")
```
LABEL=data	/media/data	ext3	users,relatime	0	2
```
this didn't work for me because i can't write anything to /media/data

my questions:
if the option "user" or "users" makes whoever mounts the drive owner of the mountpoint, who will be the owner when i type "sudo mount -a", woundn't that be root? isn't that the case also if the file system is auto mounted at bootup?
what is the difference between "user" and "users", practically?
what do i have to do now?

---

### Post by Andreas1 on 2009-02-15
OK, nevermind, now it works:

fstab:
```
LABEL=data	/media/data	ext3	defaults	0	2
```

and then:
```
sudo mkdir /media/data
sudo chmod a+rwx /media/data
```

do those file permissions sound reasonable or did i commit anything dangerous? i just noticed i should learn some things about file permissions. anyway, now it works.

---

### Post by geirha on 2009-02-15
> **Andreas1 said:**
> 
my questions:
if the option "user" or "users" makes whoever mounts the drive owner of the mountpoint, who will be the owner when i type "sudo mount -a", woundn't that be root? isn't that the case also if the file system is auto mounted at bootup?
what is the difference between "user" and "users", practically?
what do i have to do now?

From mount's manual page (man mount):
```

              user   Allow an ordinary user to mount  the  file  system.   The
                     name  of  the mounting user is written to mtab so that he
                     can unmount the file system again.  This  option  implies
                     the  options noexec, nosuid, and nodev (unless overridden
                     by  subsequent   options,   as   in   the   option   line
                     user,exec,dev,suid).

              users  Allow  every  user  to mount and unmount the file system.
                     This option implies the options noexec, nosuid, and nodev
                     (unless  overridden  by  subsequent  options,  as  in the
                     option line users,exec,dev,suid).

```

To get write access to it, just make yourself the owner ... NEVER set permissions like "chmod 777" or "chomd a+rwx". It's very unsafe. Just do:
```
sudo chmod 755 /media/data
sudo chown $USER:$USER /media/data

```
That will give you write permissions, all other users get read-only.

---

### Post by Andreas1 on 2009-02-15
> **geirha said:**
> To get write access to it, just make yourself the owner ... NEVER set permissions like "chmod 777" or "chomd a+rwx". It's very unsafe. Just do:
```
sudo chmod 755 /media/data
sudo chown $USER:$USER /media/data

```
That will give you write permissions, all other users get read-only.

thank you, i will do that...
again a few questions:
1: do i have to use chmod/chown recursively? (there are already files in /media/data)
2: chown $USER:$USER will set owner to "me" and group to "my" group. what if another (so far hypothetical) user would like to access the partition as well? is there a group for that? who else is included in my group anyhow?
3: the idea with rwxrwxrwx occured to me when i noticed that the (automatically created) mount point for my usb-hd had those permissions by default. is that because it is an ntfs disk?

edit: what if i want to r/w access that partition from another (linux) operating system? will i be allowed to do that when the owner is andreas from the ubuntu install? or do these permissions only affect the directory it is currently mounted in?
sorry i ask so many questions...:neutral:

---

### Post by Nepherte on 2009-02-15
2. If you want other users to, simply change the group ($USER) to users and make sure the other users are in the users group.
3. 777 (full) permissions is always a bad idea. It might be default behaviour of the ntfs mounting though I'm not sure.

---

### Post by geirha on 2009-02-15
> **Andreas1 said:**
> thank you, i will do that...
again a few questions:
1: do i have to use chmod/chown recursively? (there are already files in /media/data)


No, the files you've already put there has gotten default permissions which should be fine (owned by you, read/write for you, readonly for everyone else) Unless you put them there with root (e.g. using sudo).

The following command will list all files and folders not owned by you on /media/data
```
sudo find /media/data -not -user $USER -ls
```

> **Andreas1 said:**
> 
2: chown $USER:$USER will set owner to "me" and group to "my" group. what if another (so far hypothetical) user would like to access the partition as well? is there a group for that? who else is included in my group anyhow?


System -> Administration -> Users and groups.

You create a group, call it whatever you like, let's say you call it «family».
Set the group ownership and permissions of the files and folders in question. For all files and folders in /media/data:
```

sudo chgrp -R family /media/data
sudo chmod -R g+w /media/data      # Give the group write permissions

```

Then any user you add to the group «family» will get write permissions.

> **Andreas1 said:**
> 
3: the idea with rwxrwxrwx occured to me when i noticed that the (automatically created) mount point for my usb-hd had those permissions by default. is that because it is an ntfs disk?


Yes. Not actually sure why it gets listed with rwxrwxrwx, I'm fairly certain that's not the actual permissions of the ntfs partition.

> **Andreas1 said:**
> 
edit: what if i want to r/w access that partition from another (linux) operating system? will i be allowed to do that when the owner is andreas from the ubuntu install? or do these permissions only affect the directory it is currently mounted in?


Ownership of files are stored in the filesystem by the UID and GID (user id and group id). If the user on your current system has uid 1000 and you create a user on the other system with uid 1000, then that user will have the same access to the filesystem as your current user. Use the command «id» to see your uid.

> **Andreas1 said:**
> 
sorry i ask so many questions...:neutral:

Not at all, be curious!

---

### Post by Andreas1 on 2009-02-15
> **geirha said:**
> No, the files you've already put there has gotten default permissions which should be fine (owned by you, read/write for you, readonly for everyone else) Unless you put them there with root (e.g. using sudo).

files i copied there (with nautilus, not sudo, from the mentioned external ntfs drive) all had 777 permissions (owned by me), files i "created" there were 755.

so i did
```
sudo chown -R 1000:users /media/data
sudo chmod -R 775 /media/data
```

---

### Post by geirha on 2009-02-15
> **Andreas1 said:**
> files i copied there (with nautilus, not sudo, from the mentioned external ntfs drive) all had 777 permissions (owned by me), files i "created" there were 755.

so i did
```
sudo chown -R 1000:users /media/data
sudo chmod -R 775 /media/data
```

Hm, guess I was wrong then. 

Anyway, «sudo chmod -R 775 /media/data» is not quite what you want. This will set rwxrwxr-x on all files and folders. You need the execute bit on folders in order to be allowed to enter the folder, but on the files, you only want the execute bit if the file is an actual executable or a script. To fix that, you can use the find command to find all files (but not folders) inside /media/data, and remove the execute bit on each file.
```
find /media/data -type f -exec chmod -v 664 {} \;
```

EDIT: Btw, you don't need to use sudo for chmod if you own the file/folder you run it on.
EDIT2: Oh, hang on, I read your post more thoroughly. When you copy files with nautilus, it also copies the permission bits of the files, so that's the reason they had 777-permissions.

---

### Post by mad_max0204 on 2009-02-15
This is how my home partition is mounted in fstab

# /dev/sda1
UUID=168ad6a8-61ac-49f3-9912-460b05fa47d7 /home           ext3    relatime        0       2

Same options are on data and music drives but they are mounted in /home/user/Data and /home/user/Music folders.

---

### Post by caue.rego on 2009-07-28
I'm tired of looking for this info, and reading so many repeated questions and answers, telling to "never use 777" and about "defaults vs relatime", which is perfectly and easily explained on wiki about fstab... so I'll try first to ask here.

I've got a separate ext3 partition just for files, on my server, which everyone in the network should be able to have full access, including guests. I wouldn't care setting all files as 777 and I'm almost making a Cron script to do a chmod -R 777 (or maybe 775), every minute or so.

**So, anyone can tell me how can I, instead, just freaking tell the mounted partition to keep every file with a specific mode (of chmod)?** Specially the newly created ones, of course.

Just as a background info, I'm using "Back In Time" for backing up data, so I don't really care if someone accidentally deletes something, and aside I'm trying to get some GDS running for searching files so I won't care for filling it up with a mess of files too.



edit: I still have no solution for this, and I see it's a very old problem with not many answers around (none I could find): [http://ubuntuforums.org/showthread.php?t=104789&p=582873](http://ubuntuforums.org/showthread.php?t=104789&p=582873)

---

### Post by Maggiedog on 2010-04-18
Hey, caue.rego.  I think I have your answer.

So this is a really old post that nobody is likely checking anymore but I think I know and answer so here goes in case you still care (unlikely) or in case somebody else Google this issue again and this helps them (more likely).

Note: I am far far from a Ubuntu pro (it's not even the distro I use) but I think it is a more general Samba question.  

Issue:  Every time a computer from your network connects to the shared hard drive the server gives that user the "ownership" of the file it creates.  Like you said, that is annoying for anyone else who wants to change the file.  Note: The following solution only works if You really are willing to give full read/write permission to every computer with access to your server as the original poster said they were (this is likely true for most home networks).

Solution: 
1) On your server hit Alt-F2 keys
2) Select the "run in terminal" box and then type: 

sudo gedit /etc/samba/smb.conf    

3) After you hit the "run" button a terminal window should open that requires you to enter your password.  Do so.  Also, note the "login" name of the account it listed when it asked you for the password.  We'll call it "LoginABC".

4) The gedit will have opened your smb.conf file.  Early in the file you will see a line that says [global] in brackets. Add the following line below the [global] term, "force user = LoginABC"

It should now look like this:

[global]
force user = landfill

5) hit save and close the editor.  You are done.  I am a rookie at this stuff but I believe you have just told your server to ascribe the same login to everyone who uses the shared drives on your system.  It will still only give "LoginABC" ownership of the files but since it thinks everyone is "LoginABC", that really isn't a problem anymore. 

Let me know if this helps anyone.  I am new to this stuff but I have been helped by enough people on forums that it would be nice to know I had helped another.

Thanks.

---

