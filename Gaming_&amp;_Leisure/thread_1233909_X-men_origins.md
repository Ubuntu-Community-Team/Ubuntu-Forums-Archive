---
title: "X-men origins"
date: 2009-08-07
forum: Gaming &amp; Leisure
---

### Post by theprince862 on 2009-08-07
Hi every one 
i am new in ubuntu and i have x-men origins the game in an iso format image how can i mount it and install on ubuntu 9.04

---

### Post by stumbleUpon on 2009-08-07
Create a directory somewhere (e.g. home folder)
You can mount any filename.iso file using

```
mount -o loop filename.iso /path/to/directory/ 
```

If the game is a windows one, you can use "wine" to install it. See here for more info [https://help.ubuntu.com/community/WindowsGames](https://help.ubuntu.com/community/WindowsGames) and follow the links to learn more about using "wine"

---

### Post by theprince862 on 2009-08-07
Ok i did what u said and instead of path i wrote ( /media/FreeAgent Drive/GAMES/X-Men.Origins.Wolverine-RELOADED) which is the path of the iso  file and insead of the directory i created a new folder in the home folder and wrote it but it didn't work 
I know i did something wrong like i said iam new with ubuntu

---

### Post by stumbleUpon on 2009-08-07
Sorry i forgot that you need root permissions to mount an iso file.

Suppose you have an iso file called filename.iso. 

Create a directory in your home folder named XMEN.

```
mkdir XMEN 
```

Then navigate to your home directory in a terminal and type

```
sudo mount -o loop ISOPATH/filename.iso XMEN/ 
```

where ISOPATH is the complete path to the directory in which the iso file is located. You will be asked for your password. Enter that.

Go into the XMEN directory and you will then see the contents of the iso file.

If you still have problems, post back the error.

---

### Post by fennec_fox on 2009-08-07
I don't think the windows version of Xmen origins is one of the games that works on linux. The ps2 version maybe but, the windows won't run.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16507](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16507)

[http://www.cedega.com/gamesdb/games/view.html?game_id=5231](http://www.cedega.com/gamesdb/games/view.html?game_id=5231)

That's not a reason not to try. The wine page says that someone with an nvidia card might be able to get it to work.

---

### Post by theprince862 on 2009-08-07
First thanks alot for your concern
second i created the file in the home directory
then i wrote that command sudo mount -o loop /media/FreeAgent Drive/GAMES/X-Men.Origins.Wolverine-RELOADED/rld-wolv.iso XMEN/
then i got this message


Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

what can i do?
the XMEN folder in the home is empty

---

### Post by Grishka on 2009-08-07
use [Gmountiso](apt://gmountiso). there's no need to do such a basic thing with long terminal commands.

---

### Post by theprince862 on 2009-08-07
It worked thank you all for your help

---

### Post by TravisNewman on 2009-08-07
It's obvious that this is discussion of a pirated game, since it is in ISO format and has RELOADED on the end of the filename.

We do not allow discussions of illegal activity, including how to play pirated video games.

---

