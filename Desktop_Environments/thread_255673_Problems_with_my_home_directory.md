---
title: "Problems with my home directory"
date: 2006-09-11
forum: Desktop Environments
---

### Post by fiver on 2006-09-11
Ok, so this is a pretty pickle I have gotten myself into.

I used the administration tools available in gnome to change my home folders' location. The problem is I redirected it to /media/hda2 which is my second harddrive mount point, and that drive is formatted FAT32/vfat. Then I tried to log on after making the changes, and it told me that it couldn't log me on and complained that it tired to set the permissions for /media/hda2/.gnome2_private/ to 700, which was not allowed.

Now I have had the lecture about how you can't properly set permissions in fat32, so I know about this, what I haven't had is the explaination which either gives the the name of the file where ubuntu would store the information which points to where my home directory is, or tells me how to find that tool again without using gnome (I can't get my logon back at all, but I can use the xterm).

So, advice/suggestions/patient explainations to the n00b?

---

### Post by catlett on 2006-09-11
You should only have to change your /etc/fstab. The problem is, you have to know the original partition home was mounted at. Do you remember? If you know, then boot to the ubuntu login. Enter your user name and password. Then enter ```
sudo nano /etc/fstab
```
Change your home line to the original partition. 
If you do not remember the partition, enter ```
sudo fdisk -l
```That will list your partitions, maybe it will jar your memory.

---

### Post by kaitlyn on 2006-09-12
Or you can put your $HOME back where it should be, and not deal with the permission errors:

```

sudo -s
perl -pe 's/(<USER>):x:(\d+):(\d+):(.+):(.+):(.+)/$1:x:$2:$3:$4:\/home\/$1:$6/' /etc/passwd > /etc/temp-1234
mv /etc/passwd /etc/.passwd.bak && mv /etc/temp-1234 /etc/passwd
chmod 644 /etc/passwd ; chmod 644 /etc/.passwd.bak

```

The above will change the home directory for the username for '<USER>' to /home/<USER> and is all done in a terminal.

-Kat

PS:
The file that stores the home director location along with the default shell, username, default UID and GID is /etc/passwd.  Passwords are _not_ stored there on any modern UNIX system however (That would be /etc/shadow ).  Fr information on the file syntax see: [http://www.unet.univie.ac.at/aix/files/aixfiles/passwd_etc.htm](http://www.unet.univie.ac.at/aix/files/aixfiles/passwd_etc.htm)

PPS:
Those lines of code I gave you will modify that file to reset your home directory.  You can also do it manually with:
```

sudo vim /etc/passwd

```
And using the information from that site change the home directory.  Either way you'll atleast be able to log back in with your user account.

-Kat

---

### Post by fiver on 2006-09-12
Thank you very much for that :D

It turns out that for some reason my fstab file didn't contain the link (I think cos I hadn't done a good job of sorting out my home moving).

Anyway, problem fixed and thank you many times over for saving me from more drastic steps to fix things.

God Bless you.

---

