---
title: "Access for users who are children"
date: 2010-04-08
forum: Desktop Environments
---

### Post by Man with Hat on 2010-04-08
Hi,

I don't know if this belongs in the security discussion thread, but here seemed more appropriate. I am creating a new user for my son, but I don't want him to have access to M15+ games that are installed (eg Freedoom). Is there a way to deny a user's access to individual programs (or groups of programs). Also for the moment, I would really want him to only have access to a folder with his name on it and not to all of my drives and files on them. Is this possible? I couldn't find it anywhere... :confused:

---

### Post by aeiah on 2010-04-08
put his user in his own user group and disable read/write/execute permissions to your own documents and such. also, disable execute premissions to /usr/bin/freedoom or whatever

i think you can do all of it through the users and groups section of the administration menu

---

### Post by Megaptera on 2010-04-08
Hi,
Not sure how old your son is but could you set him up with his own operating system dual-booting alongside yours?
I'm thinking of Qimo - Ubuntu based o/s for kids 3yo+. Hope this isn't too unsuitable for an idea!!

[http://www.qimo4kids.com/page/What-is-Qimo.aspx](http://www.qimo4kids.com/page/What-is-Qimo.aspx)

Richard

---

### Post by Man with Hat on 2010-04-08
> **aeiah said:**
> put his user in his own user group and disable read/write/execute permissions to your own documents and such. also, disable execute premissions to /usr/bin/freedoom or whatever

i think you can do all of it through the users and groups section of the administration menu

I've just been playing around in this menu and can't seem to find anywhere that disables permissions of any sort. I have been switching between users a little and have noticed that his documents folder does not contain my documents (yes I'm a little noobie!! - and tired) however he still has access to "filesystem." I can r-click on this and select permissions, but it can't find permissions for file systems so I clicked on encryption and it takes me to "encryption and keyrings." I have no idea how this works, so I closed it :)

A cheap solution to the gaming problem I noticed though is to r-click on "applications" and then "edit menus." In here I was able to delete the shortcuts and they didn't delete on my login.

If I unmount my secondary hard drive permanently from his login will that affect mine? I want him to have read only access to the photos on this drive however. Is that possible or am I making this all too complicated?

---

### Post by Man with Hat on 2010-04-08
> **Megaptera said:**
> Hi,
Not sure how old your son is but could you set him up with his own operating system dual-booting alongside yours?
I'm thinking of Qimo - Ubuntu based o/s for kids 3yo+. Hope this isn't too unsuitable for an idea!!

[http://www.qimo4kids.com/page/What-is-Qimo.aspx](http://www.qimo4kids.com/page/What-is-Qimo.aspx)

Richard

Thanks for the idea :) I think I might have to keep it as a last resort for the time being as I would like to just keep the one operating system on here if possible. That being said, a children's operating system is a very interesting idea and I think I might check it out. I had no idea! :shock:

---

### Post by sisco311 on 2010-04-08
The executables of the games are (usually) in the /usr/games directory. 

[list=i]

[*]Create a group (i.e. *gamers*) for users allowed to run the game(s):
```
sudo addgroup gamers
```

[*]Add allowed users to the group:
```
sudo gpasswd -a **username** gamers
```
replace **username** with the login name of the user. Repeat this step for all users you want to be able to run the game(s).


[*]Log out and log back in.


[*]Change the ownership & permission of the game(s) (i.e. freedoom):
```
sudo chgrp gamers /usr/games/freedoom
sudo chmod o-x /usr/games/freedoom
```


[*]Done. Now only users from the gamers group are allowed to run freedoom.
You can read more about file permissions [here]("https://help.ubuntu.com/community/FilePermissions").

[/list]


> **Man with Hat said:**
> I want him to have read only access to the photos on this drive however. Is that possible or am I making this all too complicated?

How do you mount the driver & what filesystem is on it?

---

### Post by nothingspecial on 2010-04-08
Find out where the drive is mounted for example /media/drive

Make sure you own it ```
sudo chown -R richard:richard /media/drive
```

Then restrict everybody else, for example, I don`t mind my kids listening to the music, but I definitely don`t want them to delete it

```
chmod -R 755 /media/drive/music
```

and I don`t really want them to be able to look at my financial stuff

```
chmod -R 700 /media/drive/money
```

---

### Post by Man with Hat on 2010-07-07
> **nothingspecial said:**
> Find out where the drive is mounted for example /media/drive

Make sure you own it ```
sudo chown -R richard:richard /media/drive
```

Then restrict everybody else, for example, I don`t mind my kids listening to the music, but I definitely don`t want them to delete it

```
chmod -R 755 /media/drive/music
```

and I don`t really want them to be able to look at my financial stuff

```
chmod -R 700 /media/drive/money
```

Hi, 

thanks heaps for this, it was exactly what I was talking about. Sorry I didn't reply earlier, I have only just noticed the replies as I needed to ask a question about my boot up here. Am I to assume
755 = read only
700 = restricted (or can't see/access)

Cam

---

### Post by Man with Hat on 2010-07-07
Thanks for your reply too Sisco,

As I said to Richard in the above post, I haven't been here and wasn't aware of the reply, so I'm sorry that I didn't reply to you earlier. This is helpful info too and I am learning more about linux everyday. 

> **sisco311 said:**
> 
How do you mount the driver & what filesystem is on it?

It is an NTFS hard drive (formatted that way when windows was only operating system) I can't remember exactly how it mounts, I used a thing called "NTFS configuration tool" and that now mounts the drive during boot up for me. 

Cam

---

### Post by nothingspecial on 2010-07-07
This link explains it very well

[http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php](http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php)

However, I don`t think ntfs supports linux file permissions (I could be wrong)

As we live in a linux only household all backup drives etc are formatted ext3, with the exception of usb sticks (fat) homework and the like.

---

### Post by sisco311 on 2010-07-07
> **Man with Hat said:**
> 

It is an NTFS hard drive (formatted that way when windows was only operating system) I can't remember exactly how it mounts, I used a thing called "NTFS configuration tool" and that now mounts the drive during boot up for me. 




VFAT/NTFS partitions do not support Unix/Linux ownership and file permissions. You have to set the owner/group and permissions at mount time. The ownership and permissions will apply to all files and directories on the partition.

*NTFS configuration tool* creates an entry in the /etc/fstab file. The fourth field of the entry describes the mount  options  associated with the filesystem.

uid= Sets owner. Syntax: may use user_name or user ID #.
gid= sets group ownership of mount point. Again may use group_name or GID #.

umask= Sets the umask (the  bitmask  of  the permissions that are not present).
dmask= Sets the umask applied to directories only.
fmask= Set the umask applied to regular files only.

Syntax is "odd" at first.
To set a permissions of 777, umask=000
To set permissions of 700, umask=077

e.g. to set read/write permissions for the plugdev group and read permissions for others the entry should look like this:
```
UUID=<UUID>    /media/mount-point    ntfs-3g    defaults,gid=plugdev,dmask=002,fmask=113    0    2
```

For more info check out:
[thread=283131]How to fstab[/thread]
and
[uhelp]community/MountingWindowsPartitions[/uhelp]

---

### Post by Man with Hat on 2010-07-07
Thanks for that,

I am currently now going through the heartache of just making my machine boot up properly (read [http://ubuntuforums.org/showthread.php?t=1525153](http://ubuntuforums.org/showthread.php?t=1525153) if you are interested) so I can't try out what you have said for this. But I was wondering, as I had a similar problem with mounting my mobile phone as a mass storage device a while ago, would the same approach that you suggested work for permissions on that (FAT16 or FAT32 I can't remember which). Sometimes I couldn't mount it and times that I could, there was no way to write to it.

---

### Post by itsjoshgrant on 2010-07-07
> **Man with Hat said:**
> Thanks for the idea :) I think I might have to keep it as a last resort for the time being as I would like to just keep the one operating system on here if possible. That being said, a children's operating system is a very interesting idea and I think I might check it out. I had no idea! :shock:


ive tried qimo before and it is pretty soild os for kids (how old is he?). 
even if seems you're not looking into it as that much of an option to
 dual-boot qimo and ubuntu... you could keep your os and not make him 
an account on ubuntu and making him account in qimo instead...

just a thought
but depending on his age dual booting
 qimo might be the way to go...

---

### Post by Man with Hat on 2010-07-08
> **itsjoshgrant said:**
> ive tried qimo before and it is pretty soild os for kids (how old is he?). 
even if seems you're not looking into it as that much of an option to
 dual-boot qimo and ubuntu... you could keep your os and not make him 
an account on ubuntu and making him account in qimo instead...

just a thought
but depending on his age dual booting
 qimo might be the way to go...

He is 9 years old, so a couple of years off being able to teach me everything there is to know (so I need to stay ahead of the game! ;))

I think I may give Qimo a go, but I am currently having enough issues with my current duel boot set up with win XP. Hopefully I can sort this, back up everything, format the drive again and re-install all operating systems fresh. Then I will sleep at night to a job well done! It may sound silly, but I just want to do it all from scratch again!!!!! ](*,)

---

### Post by Man with Hat on 2010-07-08
> **nothingspecial said:**
> This link explains it very well

[http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php](http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php)

However, I don`t think ntfs supports linux file permissions (I could be wrong)

As we live in a linux only household all backup drives etc are formatted ext3, with the exception of usb sticks (fat) homework and the like.

Thanks, I just had a brief look at that and it looks very easy to follow and understand. I will certainly check it out. But as I have said to two others (starting to sound like a broken record as I typed them all today :D) I need to sort out my boot issues at the moment and then I will be able to sort all of this out. I like the link though and certainly will use it to better my linux knowledge - it is slowly slowly growing!

---

