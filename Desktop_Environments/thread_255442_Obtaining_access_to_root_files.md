---
title: "Obtaining access to root files"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Elpram on 2006-09-11
So I've put off asking the community for help for a little while, but here's my story.

I decided I wanted linux, and Ubuntu was hailed as the easiest and most popular.  After finally getting it on a bootable cd, I ran into partition problems.  I surmounted these, and managed to get ubuntu working.  I then spent some time familiarizing myself with it, as I had never before used any linux or unix distros.  I found out how to install programes with Synaptic, and by and large shied away from the terminal (about all I know how to do is cd)  I then wanted to install a plugin for aMSN.  On the site it seemed easy enough; just copy this folder into an aMSN folder.  However when I tried this, I simply couldn't.  Upon examination of the folder permissions, it was only the 'root' user that could write to this folder.  I then searched the web for answers, at which point I stumbled across something about chmod, which I of course tried, and completely killed the operating system.

Who knew I could kill an OS in under a day?

So here I am with a fresh install, and I figure I should probably ask somebody who knows what their doing before mucking about again and messing everything up.

Thanks a bunch!

---

### Post by monktbd on 2006-09-11
actually you should have a folder called .amsn in your home folder.
in that folder is also a folder called plugins where you possibly can drop the wanted folder you mentioned.

the plugin then only applies to your user and not all users but maybe that is enough for you and surely wont render your OS unuseable :).

you the plugin needs to be in the place where amsn stores its plugins then let me know.

---

### Post by Elpram on 2006-09-11
Well, for some reason there isn't an .amsn folder...only one for recieved files.  I'm not at home right now, but I believe the path to drop it in was something like /usr/share/amsn/plugins to which I don't have access.

Also, this is an entirely unrelated question that probably deserves it's own post, but is there a way for my to access the drive of my windows installation?  I want to access music and pictures and such.

---

### Post by monktbd on 2006-09-11
well all folders with a "." in front are hidden folders.
on the command line you can have a look at them with

> ls -l -a

in nautilus you can set the view to also show hidden files and folders. 

it is of course also perfectly possible to put the downloaded folder in /usr/share/amsn/plugins if it is really necessary.
this will maybe prevent a proper uninstall via synpatic though and is quite a bit more hassle to do.
i cannot guarantee that the folders are correct but it should go like

> sudo cp -r myfolder /usr/share/amsn/plugins/
when you are in the directory where your folder lies in.

you also might need to change that folder to proper rights and owners there then. 
the files there should probably owned by root, i dont know what proper permission they should have.
changing the ownership to root there:

> sudo chown -R root:root /usr/share/amsn/plugins/myfolder

no guarantee that i made all the folders right here :).


edit: about your second question:
yes you can access it, if it is ntfs you better only read from it, writing is not yet very stable.
usually they should get automatically mounted, but post 

> sudo fdisk -l
and
> cat /etc/fstab
to see what could help you.

---

### Post by Elpram on 2006-09-11
Ah, yes, I should have realized that it would be a hidden file.

As for the second answer, is there a way to do it graphically? I'm rather intimidated by this whole terminal business, seeing as I come from windows and whatnot, but if not I suppose I'd better learn it...

Thanks!

---

### Post by monktbd on 2006-09-11
> **Elpram said:**
> 
As for the second answer, is there a way to do it graphically? I'm rather intimidated by this whole terminal business, seeing as I come from windows and whatnot, but if not I suppose I'd better learn it...


some things can be done graphically.
but it is easier to give commands and explain them than pointing to a graphical program and saying click this and type this there and such.
also it is easier to give information about your system this way.

it usually should work somehow with the disk admin tool in system->administration but instead of posting several screenshots the outputs of the commands mentioned above gives usually all the information we need.
and actually i havent used it much myself so i am not much of help there as well :).

using linux without the commandline is possible but not really practical in all matters and vice versa :).

---

### Post by Lunar_Lamp on 2006-09-11
To view hidden files in nautilus (default file browser in Ubuntu) you can, in nautilus, press ctrl+h or go to View>Show Hidden Files.

---

### Post by Elpram on 2006-09-12
Well I got the hidden stuff working (although amsn doesn't work now, but I'll figure that out)

As for the hard drive, I went to the disk manager, and said enable, I then added it to my shortcuts.  However when I click on it it tells me I don't have permission to view the files.

Once again only the root user can do this.  This is rather annoying, so is there a way I can disable the whole root user thing or logon as the root user, or maybe some option that gives my user root access?

---

### Post by monktbd on 2006-09-12
> **Elpram said:**
> As for the hard drive, I went to the disk manager, and said enable, I then added it to my shortcuts.  However when I click on it it tells me I don't have permission to view the files.

Once again only the root user can do this.  This is rather annoying, so is there a way I can disable the whole root user thing or logon as the root user, or maybe some option that gives my user root access?

first: do not ever log on as root. per default the root accoutn with ubuntu is not enabled to prevent doing such a thing as working as root. this is one of the biggest problems that windows has: that the users mostly work as administrators. 

you can temporarily have root privileges with your first made user on ubuntu with writing sudo before a command. then this and only this command runs with root privileges making it a much more secure method.

the problem with your disk can be fixed quite easily, but i only know how from the commandline. i looked a bit right now into the disks application but didnt find the settings there. so if you copy and paste the results of the command listed above we will be able to help you.
>  sudo fdisk -l
and
> 
cat /etc/fstab

---

### Post by Elpram on 2006-09-12
david@david-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4552    36563908+   7  HPFS/NTFS
/dev/hda2            4553        4934     3068415   83  Linux
/dev/hda3            4935        4998      514080   82  Linux swap / Solaris
david@david-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by monktbd on 2006-09-12
ok so your ntfs partition really is not listed in fstab.
so you need to add a line in there.

first we need to have a mount point where to put the windows partition in your filesystem.

an option would be /media/windows

so this folder maybe doesnt exist so we create it:
> 
sudo mkdir /media/windows

then we need to edit your /etc/fstab

for that it needs to be in an editor that runs with root privileges.
> 
gksudo gedit /etc/fstab
accomplishes that
then add the following line
> /dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
doesnt matter where you add it, you can just put it at the end.

after saving we need to make the changes take effect:

> sudo mount -a

after that you should be able to read your windows partition.
you cannot write to it because ntfs write support isnt very stable yet.

you can maybe read a bit more at
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

or if you want to enalbe write support on that partition:
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=mount+ntfs+partition](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=mount+ntfs+partition)

---

### Post by Elpram on 2006-09-12
worked like a charm!

Thanks a whole bunch for teaching me the ropes!

---

