---
title: "(linux noob) How to store steam games on different partition?"
date: 2014-03-22
forum: Gaming &amp; Leisure
---

### Post by jamie14 on 2014-03-22
My 500gb windows HDD was corrupted, so I formatted it, and changed it to Ext4. I have my ubuntu and steam on my 24GB SSD, and only have ~10gb to play with, not enough for even one of my steam games. 

Is it possible to save games to my newly formatted ext4 HDD? I'm a complete noob, but I think it has something to do with fdisk?

As it is right now, I have my new HDD mounted but I can find no way of letting steam know I want to store games there.

---

### Post by drmrgd on 2014-03-22
I have not yet tried this yet (have to do it soon, though as I'm nearly out of space!), but I think you can do this by changing the 'Content Libraries' directory in the Steam settings menu.  From the top, go to Steam -> settings, and click the "Downloads" link in the left-hand pane.  You can then choose to "Add Library Folder", which will bring up a directory browser from which you should be able to select your new HDD.

---

### Post by jamie14 on 2014-03-22
hey thanks for the quick reply, I've tried that but I can't find my HDD within it just starts from root and my disk isnt in there (i'm a complete noob so bear with me haha)

I think it has something to do with copying some part of .steam to my new partition, but I can't put my finger on it exactly...I KNOW it can be done, so there's that !

---

### Post by MikeCyber on 2014-03-23
I simply moved the Steam folder to another disc with enough free space and did a symlink. ln -s something sowmeher have a look at: man ln
Something alike: ln -s /whereever/Pictures .
the . means to here.



michael@michael-Ubuntu:~$ cd .steam
[EMAIL="michael@michael-Ubuntu:~/.steam"]michael@michael-Ubuntu:~/.steam[/EMAIL]$ ls -la
total 36
drwxrwxr-x  2 michael michael  4096 Feb 16 10:37 .
drwxr-xr-x 76 michael michael 12288 Mar 23 08:40 ..
lrwxrwxrwx  1 michael michael    26 Feb 16 10:36 bin -> /home/michael/.steam/bin32
lrwxrwxrwx  1 michael michael    29 Feb 16 10:36 bin32 -> /media/DATA/Steam/ubuntu12_32
lrwxrwxrwx  1 michael michael    29 Feb 16 10:36 bin64 -> /media/DATA/Steam/ubuntu12_64
-rw-rw-r--  1 michael michael  1035 Feb 16 10:41 registry.vdf
lrwxrwxrwx  1 michael michael    17 Feb 16 10:36 root -> /media/DATA/Steam
lrwxrwxrwx  1 michael michael    25 Feb 16 10:36 sdk32 -> /media/DATA/Steam/linux32
lrwxrwxrwx  1 michael michael    25 Feb 16 10:36 sdk64 -> /media/DATA/Steam/linux64
lrwxrwxrwx  1 michael michael    17 Feb 16 10:36 steam -> /media/DATA/Steam
-rw-------  1 michael michael  8822 Aug  8  2013 steam_install_agreement.txt
-rw-rw-r--  1 michael michael     5 Feb 16 10:36 steam.pid
prw-------  1 michael michael     0 Feb 16 10:37 steam.pipe
[EMAIL="michael@michael-Ubuntu:~/.steam"]michael@michael-Ubuntu:~/.steam[/EMAIL]$ pwd
/home/michael/.steam
[EMAIL="michael@michael-Ubuntu:~/.steam"]michael@michael-Ubuntu:~/.steam[/EMAIL]$

---

### Post by drmrgd on 2014-03-23
How do you have your external HDD mounted (i.e. what is the fstab entry)?  Assuming you have it mounted to a location in /media, it should be fairly straightfoward from there.  I think the easiest way is as follows:

1. get the UUID of your drive:

```

sudo blkid

```

You should see a list of partitions and the UUID of the drive, which would look something like:

```

/dev/sdc3: UUID="fd8869bb-cfd6-4f52-9762-9a3ff9e7f5b4" TYPE="ext4"

```

If you're not quite sure what partition you need to mount (e.g. is it /dev/sda1 or /dev/sdb1 or whatever), you can probably figure that out by running:

```

sudo fdisk -l

```

which will give you a more detailed listing of the drives that are attached.

2. Make a directory in /media to act as the mount point for that drive:

```

sudo mkdir /media/<whatever_you_want_to_call_it> && sudo chown $USER:$USER /media/<directory_you_are_creating>

```

That will create a new directory in /media to act as your mount point, and give ownership to you (default is root) so that you can read and write to it.  

3.  Now with that, you can create the entry in fstab.  Using the UUID you got in step 1, and the new directory you created in step two, create an entry in fstab with any text editor you like.  Remember that root owns that file, so you'll need to use sudo to edit it (use gksudo if you want to use gedit).  The entry should look like this (replace with the appropriate information; I'll use a directory called test in this case):

```

# My Steam library drive
UUID=30a5a1fa-4afe-4509-9412-9f139261f3e1    /media/test    ext4    defaults    0    0

```

4.  Now mount that drive by using:
```

sudo mount /media/<your_new_mount_point>

```

At this point, we now have your new drive mounted to /media/<what_ever_you_called_your_mountpoint>, and that should be visible in that file browser within Steam.  At this point, I'm assuming it's as simple as just selecting that directory and depositing your game files there, but I have not yet done this, so it's a little bit of a guess from here on.

Let us know if that helps and / or you run into any problems along the way.

---

### Post by oldrocker99 on 2014-03-23
I moved my Steam folder to a second partition. I started Steam and it said, "Cannot Find your Steam folder. Perhaps you moved it?" It put up a file manager window, I pointed to the moved folder, and all was well.

---

