---
title: "login screen just loops"
date: 2021-05-12
forum: Desktop Environments
---

### Post by wrhite on 2021-05-12
My login screen accepts my password and after a short while of blank screen returns to the login again.
I can get to the shell with ctrl-alt-F3 and al seems well.
From there I can do sudo startx and get a desktop of sorts but it is with a username of root which is not much use

I looked at the journal and see this little snippet
```

May 12 15:55:23 william-OptiPlex-7010 gnome-screensav[2243]: Couldn't get presence status: The name org.gnome.SessionManager was not provided by any .service files
May 12 15:55:23 william-OptiPlex-7010 dbus-daemon[2119]: [session uid=1000 pid=2119] Successfully activated service 'org.gnome.ScreenSaver'
May 12 15:55:23 william-OptiPlex-7010 gnome-session[2122]: Failed to write file “/home/william/.local/share/session_migration-ubuntu.K0ZT20”: write() failed: No space left on device
May 12 15:55:24 william-OptiPlex-7010 gnome-keyring-daemon[2103]: error writing to `/home/william/.local/share/keyrings/.#lk0x5556767847a0.william-OptiPlex-7010.2103': No space left on device
May 12 15:55:24 william-OptiPlex-7010 gnome-keyring-daemon[2103]: couldn't create lock for store file: /home/william/.local/share/keyrings/user.keystore: Bad file descriptor
May 12 15:55:24 william-OptiPlex-7010 gnome-keyring-daemon[2103]: couldn't open store file: /home/william/.local/share/keyrings/user.keystore: Bad file descriptor
May 12 15:55:24 william-OptiPlex-7010 gnome-keyring-daemon[2103]: file pkcs11/gnome2-store/gkm-gnome2-storage.c: line 1387 (gkm_gnome2_storage_token_flags): should not be reached
May 12 15:55:24 william-OptiPlex-7010 gnome-keyring-daemon[2103]: error writing to `/home/william/.local/share/keyrings/.#lk0x555676777060.william-OptiPlex-7010.2103': No space left on device
May 12 15:55:24 william-OptiPlex-7010 gnome-keyring-daemon[2103]: couldn't create lock for store file: /home/william/.local/share/keyrings/user.keystore: Bad file descriptor
May 12 15:55:24 william-OptiPlex-7010 gnome-keyring-daemon[2103]: couldn't initialize slot with master password: The operation failed
```

I don't understand why it says out of space - there are ca 40GB free on that drive. BUT I have suspicions about snap loop devices being counted against the drive allocation.

If it is of any significance I have three partitions: one for / and another, much larger, for /home and one for swap.

Help and suggestions gratefully accepted! I'm tearing my hair out over this.

---

### Post by grahammechanical on 2021-05-12
Snap applications will take up space on the hard disk just like all the other applications and utilities installed as part of the operating system. Set against that, I do not think that snap loop devices take up space on the hard disk. They will use some small amount of system memory (RAM) until the snap application is loaded, then it will take up even more memory. Just like as other applications do when loaded or opened.

The "no space left on device" message is in reference to the keyrings folder in /home. How large is the home partition? How much space is available in the home partition. There is a Disk Usage Analyser utility that might prove useful. You would have to use a Ubuntu live session. Or, run some command from a TTY.

Regards

---

### Post by Frogs Hair on 2021-05-13
Using the following command may provide some insight.  

```
df -h
```

---

### Post by ActionParsnip on 2021-05-13
Also add the output of:
```

df -i

```

---

### Post by wrhite on 2021-05-17
Thanks for suggestions. I solved it.

Du and Df were  showing massive discrepancies. And most perplexingly df had a weird set  of numbers: Similar to this (from a different machine)
```
[FONT=lucida console]Filesystem                  Size  Used    Avail Use% Mounted on
/dev/sdb1                   458G  346G   89G  80%   /extras
/dev/sda1                   472M 378M  70M  85%   /boot[/FONT]
```

this may not look odd but do the maths - e.g. 346/458 is 77.5% and 378/472 80.1% - so there is a 5% discrepancy

On  my failing /home drive of some 950Gb the available space reported by df  was 40gb and %used reported as 100%. Thus despite there being 40gb  unused the disk was counted as full.

The solutions described all  over the web are many and various, hidden/locked files, spurious mount  points etc - see here for a typical compilation  [https://serverfault.com/questions/275206/disk-full-du-tells-different-how-to-further-investigate](https://serverfault.com/questions/275206/disk-full-du-tells-different-how-to-further-investigate)

But  the answers that really were simple and worked were just like this  [https://odzangba.wordpress.com/2010/02/20/how-to-free-reserved-space-on-ext4-partitions/](https://odzangba.wordpress.com/2010/02/20/how-to-free-reserved-space-on-ext4-partitions/)  or this  [https://ma.ttias.be/change-reserved-blocks-ext3-ext4-filesystem-linux/](https://ma.ttias.be/change-reserved-blocks-ext3-ext4-filesystem-linux/)

** Disk reservation is the culprit** - hardly needed on a non root device at all and certainly not at 5% on a 1Tb drive only being used for /home.

There  is a longer discussion of the issue here  [https://www.redhat.com/sysadmin/disk-space](https://www.redhat.com/sysadmin/disk-space) showing this snippet which  was very much like mine. 

```

[root@somehost ~]# df -h
Filesystem             Size  Used  Avail  Use%  Mounted on 
/dev/sda6              991M  924M     0  100%  /home
```

So I did a
> tune2fs -m 1 /dev/sda6  

i.e  reducing the reserved space to 1% as opposed to 5% and now bingo! the Gnome  desktop has plenty of space to write all its needed files to complete  the login properly.

Thanks again for your help.

---

