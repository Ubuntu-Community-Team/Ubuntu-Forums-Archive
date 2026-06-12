---
title: "Permissions on a shared directory"
date: 2006-03-16
forum: Desktop Environments
---

### Post by mjwood0 on 2006-03-16
Okay...  this should be easy and I'm sure I'm just missing something.

**Situation**
My Linux box is used by both my wife and I.  I created a partition (/dev/sda5) for shared data such as music and photos.  I want us both to be able to add, delete and modify anything in these folders.  The partition is mounted in /home/data and contias two directories -- photos and music.

From my understanding, the correct way to do this is via groups.  So I created a group called "data" and performed a chgrp on the /home/data directory.  So far, so good.  I also added myself and my wife to this group.

However, I then had to change the permissions for the group on both subdirectories to allow full access to everyone in the group.  All works to this point.

**Problem**
I decided to copy all my backed up music onto this new computer in the /home/data/music directory.  Every file I create has the group permissions set wrong.  Every file / folder my wife would create would also have the same problems.  So now I'm stuck.  I don't want her to have to chmod everything she adds and I don't want to have to remember to do this either.

What's the obvious and quick answer I'm overlooking?  I can re-organize anything if I did that part wrong.  

Thanks in advance!

---

### Post by aysiu on 2006-03-16
Based on the wee bit of Google research I just did, my guess is that it would be ```
sudo cp /etc/profile /etc/profile_backup
sudo gedit /etc/profile
``` and then changing the bottom line from ```
umask 022
``` to ```
umask 002
``` **Please**, do not follow this advice until someone else chimes in and says, "That sounds like a good idea."

I'm not 100% sure that'll work, and I'd rather have someone more knowledgeable about Ubuntu confirm that it's worth a shot before you might bork your system.

**Edit**: It may actually be in a different file (/etc/login.defs), but it appears to be commented out (if that # sign means what I think it does)... ```
# Login configuration initializations:
#
#	ERASECHAR	Terminal ERASE character ('\010' = backspace).
#	KILLCHAR	Terminal KILL character ('\025' = CTRL/U).
#	UMASK		Default "umask" value.
#	ULIMIT		Default "ulimit" value.
#
# The ERASECHAR and KILLCHAR are used only on System V machines.
# The ULIMIT is used only if the system supports it.
# (now it works with setrlimit too; ulimit is in 512-byte units)
# 
# UMASK usage is discouraged because it catches only some classes of user
# entries to system, in fact only those made through login(1), while setting
# umask in shell rc file will catch also logins through su, cron, ssh etc.
#
# At the same time, using shell rc to set umask won't catch entries which use
# non-shell executables in place of login shell, like /usr/sbin/pppd for "ppp"
# user and alike.
#
# Therefore the use of pam_umask is recommended (Debian package libpam-umask)
# as the solution which catches all these cases on PAM-enabled systems.
# 
# This avoids the confusion created by having the umask set
# in two different places -- in login.defs and shell rc files (i.e.
# /etc/profile).
#
# For discussion, see #314539 and #248150 as well as the thread starting at
# http://lists.debian.org/debian-devel/2005/06/msg01598.html
#
# Prefix these values with "0" to get octal, "0x" to get hexadecimal.
#
ERASECHAR	0177
KILLCHAR	025
# 022 is the "historical" value in Debian for UMASK when it was used
# 027, or even 077, could be considered better for privacy
# There is no One True Answer here : each sysadmin must make up his/her
# mind.
#UMASK		022
#ULIMIT		2097152
```

---

### Post by mjwood0 on 2006-03-16
That would work -- except that it would change it for ALL files written.

I wanted to use the umask=0000 in the fstab file for that entry, but it seems that I get an error since the file system type is ext3.

With the following line in my /etc/fstab file:
```
/dev/sda5       /home/data      ext3    defaults,umask=0000        0     0
```

I get an error when remounting using the command:
```
sudo mount -a
```

The error from the dmesg file is:
```
[17228893.196000] EXT3-fs: Unrecognized mount option "umask=0000" or missing value
```

I know this would work with a vfat type filesystem, but it seems not to work with an ext3.

Thanks for the help though!  I really do appreciate any and all advice!

---

### Post by aysiu on 2006-03-16
Can you try... ```
/dev/sda5       /home/data      ext3    umask=002        0     0
```?

---

### Post by mjwood0 on 2006-03-16
@aysiu -- This problem really was bothering me for a week or so and I decided to post tonight.  At the same time, I've been doing more research and have since learned that ext2 / ext3 filesystems are not compatable with the umask option in the fstab file.

Not really sure where to go here.  I have heard something about acl (POSIX Access Control Lists) and that these are the solution, but I'm really not familiar at all with this!

Perhaps when / if I get this figured out, I'll have to write a howto or somehting.

---

### Post by aysiu on 2006-03-16
You said you did a *chgrp.*

Have you tried a *chown* of the directory? ```
sudo chown -R mjwood:data /home/data
```

This assumes, of course, that your username is *mjwood* and that the group you and your wife share is called *data*.

**Edit**: no, that doesn't work. I just tested it.

---

### Post by jrib on 2006-03-16
just some information but no real solution for your problem.

afaik:
/etc/profile won't get sourced when you login to gnome (login.defs does and I am not sure where umask gets set -_-).  And like mjwood0 said that would affect all the files he created.

the umask option in fstab isn't valid on an ext3 filesystem


I'll poke man chmod and edit this if I find something :).  To be clear you want everyone to have read write and execute permissions to all the files contained in /home/data (edit: regardless of whether you or your wife owns the file)?

---

### Post by aysiu on 2006-03-16
[QUOTE=_jason]To be clear you want everyone to have read write and execute permissions to all the files contained in /home/data?[/QUOTE] If I'm understanding mjwood correctly, I believe he wants anyone in his "group" (he and his wife) to be able to read/write all files created by people in that group--in other words, to have chmod 775 be the default, as opposed to chmod 755.

---

### Post by mjwood0 on 2006-03-16
**Solution!!!**
Well, I guess I'm going to answer my own question -- but am also going to make sure I post it so others may benefit.

The solution is ACL -- POSIX Access Control Lists

Now -- I must say, I don't really fully understand all the features here.  But they are quite powerful and were pretty easy to make work in my situation.

So, to start with, download acl.
```
sudo apt-get install acl
```

At this point, you have to modify your fstab file for the mount you want to be able to use ACL.  But first, unmount this folder.
```
sudo umount /dev/sda5
```

You will obviously have to replace "sda5" with the appropriate partition.

Then, edit the fstab file to add "acl" to the mount options.  It should look like this:
```
/dev/sda5       /home/data      ext3    defaults,acl    0     0
```

At this point, you need to re-mount the drives.  Easy way is:
```
sudo mount -a
```

Okay.  So you're back in business.  In my case the directory I want to be read, write, execute for everyone in the group "data" is /home/data.

To see the acl permissions on this file, do the following:
```
mjwood@mojave7:~$ getfacl /home/data
getfacl: Removing leading '/' from absolute path names
# file: home/data
# owner: root
# group: data
user::rwx
group::rwx
other::r--
```

This pretty much tells you the same thing as a "ls -al" command.

What I wanted to do, was set the default permissions on the directory to rwx for all users in the "data" group.

```
sudo setfacl -dm g:data:rwx /home/data
```

Repeating the getfacl command now gives me this:
```
getfacl /home/data
getfacl: Removing leading '/' from absolute path names
# file: home/data
# owner: root
# group: data
user::rwx
group::rwx
other::r--
default:user::rwx
default:group::rwx
default:group:data:rwx
default:mask::rwx
default:other::r--
```

From what I can tell, the options mean the following:
-d  -- Set the default permissions
-m -- Modify the selected permission

the rest of the command is as follows:
"g" is that I want to set permissions based on a group
"data" is the group I want to set the permissions for
"rwx" are the permissions I want to set.

Just an important note in case anyone tries this -- to remove acl permissions, execute the following on the directory:
```
sudo setfacl -b /directory/to/remove/permissions/from
```

I tested this and everything under this directory inherits the default permissions.  Works great for what I want!

Now I just have to see if this survives a reboot...

Hope this helps.  If I get a chance, I'll try to write my first howto -- that is if anyone thinks it would be useful!

---

### Post by aysiu on 2006-03-16
I'm bookmarking this thread in case someone asks again.

---

### Post by jrib on 2006-03-16
[QUOTE=mjwood0]**Solution!!!**
Hope this helps.  If I get a chance, I'll try to write my first howto -- that is if anyone thinks it would be useful![/QUOTE]

Ah very nice to know, and I'm sure it will be very useful to others.  Good job.

---

### Post by andmer on 2006-04-03
[QUOTE=mjwood0]**Solution!!!**
Well, I guess I'm going to answer my own question -- but am also going to make sure I post it so others may benefit.

The solution is ACL -- POSIX Access Control Lists

Now -- I must say, I don't really fully understand all the features here.  But they are quite powerful and were pretty easy to make work in my situation.

So, to start with, download acl.
```
sudo apt-get install acl
```

At this point, you have to modify your fstab file for the mount you want to be able to use ACL.  But first, unmount this folder.
```
sudo umount /dev/sda5
```

You will obviously have to replace "sda5" with the appropriate partition.

Then, edit the fstab file to add "acl" to the mount options.  It should look like this:
```
/dev/sda5       /home/data      ext3    defaults,acl    0     0
```

At this point, you need to re-mount the drives.  Easy way is:
```
sudo mount -a
```

Okay.  So you're back in business.  In my case the directory I want to be read, write, execute for everyone in the group "data" is /home/data.

To see the acl permissions on this file, do the following:
```
mjwood@mojave7:~$ getfacl /home/data
getfacl: Removing leading '/' from absolute path names
# file: home/data
# owner: root
# group: data
user::rwx
group::rwx
other::r--
```

This pretty much tells you the same thing as a "ls -al" command.

What I wanted to do, was set the default permissions on the directory to rwx for all users in the "data" group.

```
sudo setfacl -dm g:data:rwx /home/data
```

Repeating the getfacl command now gives me this:
```
getfacl /home/data
getfacl: Removing leading '/' from absolute path names
# file: home/data
# owner: root
# group: data
user::rwx
group::rwx
other::r--
default:user::rwx
default:group::rwx
default:group:data:rwx
default:mask::rwx
default:other::r--
```

From what I can tell, the options mean the following:
-d  -- Set the default permissions
-m -- Modify the selected permission

the rest of the command is as follows:
"g" is that I want to set permissions based on a group
"data" is the group I want to set the permissions for
"rwx" are the permissions I want to set.

Just an important note in case anyone tries this -- to remove acl permissions, execute the following on the directory:
```
sudo setfacl -b /directory/to/remove/permissions/from
```

I tested this and everything under this directory inherits the default permissions.  Works great for what I want!

Now I just have to see if this survives a reboot...

Hope this helps.  If I get a chance, I'll try to write my first howto -- that is if anyone thinks it would be useful![/QUOTE]

hi there,

I read your howto regarding ACL and I would like to know if, according to you, it is possible to use that method also with NFS.
As a matter of fact I have some problem with permissions. I can not set umask in such a way that every user belonging to the same group can create files with the permissions that I wish.
Do u think that adding the umask to fstab file could help me? Does nfs support umask?
This is the raw interested in the fstab file:

192.168.2.100:/home/share /media/nfs nfs rw,hard,intr      0       0

Ciao

Andrea

---

### Post by Roman27 on 2006-06-28
I would like to add my 2 cents briefly to this thread.  Maybe someone (or I) can add these tid-bits of wisdom to the wiki at some point.

Ok, like mjwood0, my wife and I share a dedicated drive on my Ubuntu machine over a small home LAN.  She uses Windows XP.  I haven't convinced her to convert yet.  ;-)   She connects to my Ubuntu box via a Samba share I've set up for her.  Anyway, like mjwood0, we've had our run-in with getting the setup to work just right.  Thankfully, I ran across this thread and it helped me out.  But, I went a little further with my customization and want to add my solution here.  Here's my story.

Like I said above, I share a dedicated drive with my wife over our home LAN.  It's been that way for quite sometime.  In fact, it was that way before I switched from Windows XP.  Previously, I had everything set up on FAT32, but had problems every now and then with Ubuntu locking up while writing to that disk.  I couldn't figure it out for the longest time.  Then one day, I ran across an article that said that the Linux driver for FAT32 had trouble with FAT32 partition sizes larger than 128GB.  Well, I had formatted the entire 160GB drive as one large FAT32 partition back in the days of Windows XP.  Oh well, I guess with all the important things that I have on the drive now it was time to switch to a more robust filesystem anyway.

Thinking things would be easy, I took another drive (250GB) I had previously in my TiVo and set about formatting it with XFS and copying all the files from my 160GB FAT32 drive to the new 250GB XFS drive.  I did this task while booted from a Dapper Live CD so I could run the latest GParted and XFS tools to setup the new drive.

Problem #1, after removing the 160GB drive and then booting to Ubuntu 5.10 again with the correct fstab entry for the new 250GB drive, I found that my files were all owned by some user and group named 999.  No problem!  I decided that I would create a group called "data" and add my account and my wife's Samba enabled account to it.  Then I ran the following command to give us both permission to the files via the data group I just created:```
sudo chown -R root:data .
```and:```
sudo chmod -R 664 .
```
That's it, right?  Wrong! :(  I had just set all my directories to permissions that didn't include the execute bit.  #-o   After some digging and testing, I ran the following command to fix it:```
sudo find . -type d -exec chmod 775 {} \;
```
That was it now, right?  Wrong!  :(  Everytime I (or my wife) created a file or directory it would be under our account for both the owner and the group.  Some more digging revealed that the sticky-group-bit was what I wanted to make the data group inheritable to newly created files and folders.  So, I ran the following command to fix it all up:```
sudo find . -type d -exec chmod 2775 {} \;
```
Ok, now I'm done, right?  Wrong!  Everytime I made a file, it would give it permissions according to my umask (0022), which means the group I setup, data, doesn't have permission to modify the files I add to our share.  I REALLY didn't want to change my umask, because that would apply to EVERY file I create anywhere in the system.  I needed a special umask for this drive only.  But, I found out that although I was able add a special parameter to the fstab for the previous FAT32 drive, that won't work with XFS (or any other file system except NTFS).  It's at this point that I ran across the thread I'm now adding to.

What I needed was ACL control.  So, I followed the instructions in the post above and added ACL.  I also added [Eiciel]("http://rofi.pinchito.com/eiciel/?s=5"), which is an extension to Nautilus for editing ACLs graphically.  (Although, I have to say, I prefered the command line.  Eiciel was a bit confusing for me.)  After adding the ACL tools, I was ready to go.  It turns out XFS has it already enabled by default, so there was no need to reboot or add a parameter to turn it on in the fstab file.

After some **heavy** research ([http://www.vanemery.com/Linux/ACL/linux-acl.html](http://www.vanemery.com/Linux/ACL/linux-acl.html)) and a good deal of trial and error, I ran this command:```
sudo setfacl -d --set u::rwx,g::rwx,o::rx .
```
Ahh things were working now!  :grin:  Until my wife started making files via Samba!  #-o  Once again, after researching thoroughly, I found out that by default Samba sets file permissions to 600 and directory permissions to 700.  Thankfully, there are parameters to put in the smb.conf file to change that behavior.  Here's a snip from my smb.conf file that defines the share for my drive:```
[D]
path = /media/data
browseable = yes
writable = yes
create mask = 0664
directory mask = 0775
```
Is that it now?  Finally?  Yep, that did it.  Now my wife and I can both access the files on our shared drive, which is formatted with a robust journalling file system that supports permissions.  No matter who creates the file or who is owner, it inherits the data group via the sticky bit and, thanks to ACL, that group inherits read and write permission on all files created on the drive.  Ahhh...  A lot of hard work and research, but it all paid off in the end.  :grin:  I hope you can benefit from it too.

---

### Post by Akula on 2006-07-09
> **mjwood0 said:**
> **Solution!!!**
```
getfacl /home/data
getfacl: Removing leading '/' from absolute path names
# file: home/data
# owner: root
# group: data
user::rwx
group::rwx
other::r--
default:user::rwx
default:group::rwx
default:group:data:rwx
default:mask::rwx
default:other::r--
```


How did you set 'default:group::rwx' ? I got only 'default:group::r-x' (all the other things looks like to be in same way)

No problems anymore... Rebooted and it was OK.

---

### Post by gmallard on 2006-10-17
I found this quite useful.

Am fairly new to Ubuntu, bit an experienced Linux user.

Regarding the UMASK 0002 idea:  That can be made to work.  I think of it as the 'RedHat' way.  The concept of 'user private groups' is implemented using a system wide UMASK of 0002.

When the shared directory is then created, something like the following would need to also be done:

chown root.sharegroup shareddir
chmod 2775 shareddir

Note that the GID bit is (first) set on the top level directory before use.

This can actually work onan Ubuntu system - I have one set up exactly as described, because it was my first Deb system, and I only knew RedHat.

The acl method works almost exactly the same.  The initial directory needs perms of 775 (no GID bit required).  I think that is missing from the discussion.

When I first read this, I thought it might have to be done on a whole partition basis.  It does not - subdirectories can be managed like this or not - but the change to mount attributes is required.

One other surprising effect.  Using the UMASK scheme, the group owner of new files shows as the group name.  Using the acl scheme, the group owner shows as the default group of the creating user.

---

### Post by skathrein on 2006-12-01
> **mjwood0 said:**
> **Solution!!!**
Well, I guess I'm going to answer my own question -- but am also going to make sure I post it so others may benefit.

The solution is ACL -- POSIX Access Control Lists

Now -- I must say, I don't really fully understand all the features here.  But they are quite powerful and were pretty easy to make work in my situation.

So, to start with, download acl.
```
sudo apt-get install acl
```

At this point, you have to modify your fstab file for the mount you want to be able to use ACL.  But first, unmount this folder.
```
sudo umount /dev/sda5
```

You will obviously have to replace "sda5" with the appropriate partition.

Then, edit the fstab file to add "acl" to the mount options.  It should look like this:
```
/dev/sda5       /home/data      ext3    defaults,acl    0     0
```

At this point, you need to re-mount the drives.  Easy way is:
```
sudo mount -a
```

Okay.  So you're back in business.  In my case the directory I want to be read, write, execute for everyone in the group "data" is /home/data.

To see the acl permissions on this file, do the following:
```
mjwood@mojave7:~$ getfacl /home/data
getfacl: Removing leading '/' from absolute path names
# file: home/data
# owner: root
# group: data
user::rwx
group::rwx
other::r--
```

This pretty much tells you the same thing as a "ls -al" command.

What I wanted to do, was set the default permissions on the directory to rwx for all users in the "data" group.

```
sudo setfacl -dm g:data:rwx /home/data
```

Repeating the getfacl command now gives me this:
```
getfacl /home/data
getfacl: Removing leading '/' from absolute path names
# file: home/data
# owner: root
# group: data
user::rwx
group::rwx
other::r--
default:user::rwx
default:group::rwx
default:group:data:rwx
default:mask::rwx
default:other::r--
```

From what I can tell, the options mean the following:
-d  -- Set the default permissions
-m -- Modify the selected permission

the rest of the command is as follows:
"g" is that I want to set permissions based on a group
"data" is the group I want to set the permissions for
"rwx" are the permissions I want to set.

Just an important note in case anyone tries this -- to remove acl permissions, execute the following on the directory:
```
sudo setfacl -b /directory/to/remove/permissions/from
```

I tested this and everything under this directory inherits the default permissions.  Works great for what I want!

Now I just have to see if this survives a reboot...

Hope this helps.  If I get a chance, I'll try to write my first howto -- that is if anyone thinks it would be useful!

I just found this with some other posts and it does seem to be the best way.  Just wanted to add that [eiciel]("http://rofi.pinchito.com/eiciel/") is a graphical way of dealing with the acl stuff.  It can be installed using synaptic.

---

### Post by penkie on 2007-05-18
This is a very interesting post because it describes almost exactly what I want to do. 

However, there is one difference. I only have one big drive and prefer not to subpartition it (i.e. just for this sharing issue). Does anyone know if it would be a problem if I do this acl-procedure for my root-driver?

-edit- To answer my own question: I just went ahead and tried it and it works like a charm. :-)

---

### Post by alex.vice.grab on 2007-08-06
Hello,

I have used the method above (using setfacl) to create a folder, in my case /home/family for the group 'family' to use.  When I create, download or import (from a device) files everything works fine and the permissions are set correctly (rwx).
However, when I try to copy files onto the directory that already have had a permission assigned (e.g. r-- for the default group of my user, 'family') to them (for instance, if I copy a file from my desktop to /home/family), it does not change the permissions.  Is there any way to make it automatically change the permissions (from r--, which is the default for files created on my own desktop/home, to rwx)?
Or at least, is there one single command to set the permissions of the folder and all sub-folders and files to have the group 'family' to have rwx permissions? (something like 'sudo chmod etc...')

Thank you in advance!
Alejandro

---

### Post by aysiu on 2007-08-06
> **alex.vice.grab said:**
> 
Or at least, is there one single command to set the permissions of the folder and all sub-folders and files to have the group 'family' to have rwx permissions? (something like 'sudo chmod etc...') ```
sudo chmod -R 775 /home/family
```

---

### Post by clievers on 2007-08-08
eeh, no way to do this other then acl?
i'm currently having this exact issue.

---

### Post by DemoN3x on 2007-08-26
> **mjwood0 said:**
> **Solution!!!**
Well, I guess I'm going to answer my own question -- but am also going to make sure I post it so others may benefit.


The solution is ACL -- POSIX Access Control Lists

----> Snip

Hope this helps.  If I get a chance, I'll try to write my first howto -- that is if anyone thinks it would be useful!


Excellent, just the thing I needed.  Worked right away :D

---

### Post by clievers on 2007-08-26
yes, the acl seems to work

---

### Post by kenzo.matuzawa on 2007-09-09
Yeah, the acl seems to work, but the gmallard way to do is far easier, just do:

sudo mkdir <dir>
sudo chown root.users <dir>
sudo chmod 2775 <dir>

And works after reboot, and doesn't need acl!

---

### Post by DemoN3x on 2007-09-12
> **kenzo.matuzawa said:**
> Yeah, the acl seems to work, but the gmallard way to do is far easier, just do:

sudo mkdir <dir>
sudo chown root.users <dir>
sudo chmod 2775 <dir>

And works after reboot, and doesn't need acl!

This does not work for multiple users downloading/sharing the same directory.  I tried several ways and the only one which was reliable was using ACL.  Unless you wish to keep resetting permissions everytime you log back in and there are new items in the shared folder.

---

### Post by peterroots on 2007-12-03
Oh you lovely person!
I have been trying to do this using eiciel which just seemst to set the permissions(using acl) for the file or folder.  it is not inherited so new files and folders default to the traditional user:group settings as per chown/chmod which is very irritating as acl seemed to be just the answer I was looking for.
I shall try your setfacl method out as see what happens but it sounds just what I want!

---

### Post by Roger Mudd on 2008-01-08
In a similar situation and I'd love to give this a shot but I'm running into a problem. Whenever I try to unmount the drive on which the target directory is located I get the following message:

```

umount: /home: device is busy
umount: /home: device is busy

```

The target directory is located on a RAID 1 array. Any ideas?

---

