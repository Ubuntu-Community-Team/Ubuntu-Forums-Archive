---
title: "unable to access to floppy disk"
date: 2005-11-03
forum: Desktop Environments
---

### Post by mxyzptlk on 2005-11-03
well ubuntuers i need help:

everytime i try to access to floppy i get this message:

"impossible to mount selected device"

and in details it says

"UDI introduced is not a mountable volume"

any suggestion

10x in advanced

---

### Post by hajk on 2005-11-03
It's a known bug, so for now you'll just have to mount the floppy manually with the command (in a terminal, or type it in with Alt-F2)

"mount /media/floppy"

at least if you have the default Breezy setup. This may sometimes fail to detect the file system (msdos) properly, so then you'll have to use the command

"sudo mount -t msdos /dev/fd0 /media/floppy"

The floppy drive icon then appears on the desktop, you can click on it and a Nautilus window will open. Right clicking on the icon will give you a menu with which you can unmount this volume.

I would expect a fix for this bug soon, but you shouldn't hold your breath waiting for it...;)

---

### Post by paddyg on 2005-11-03
the bug fix has been available for some time now.

you've got to enable---for once (then comment the line)--- the following dapper repository in /etc/apt/sources.list

```
deb http://archive.ubuntu.com/ubuntu dapper main restricted
```

then just use synaptic to download and install

pmount 0.9.6-1

PS: on my box it works fine!

---

### Post by mxyzptlk on 2005-11-03
thanks a lot to both i will try the two options

---

### Post by mxyzptlk on 2005-11-03
thank you so much floppy is working now 

thanks for the repository

---

### Post by emcvlt on 2005-11-09
Hi

Change this line in /etc/fstab:

/dev/fd0        /media/floppy0  auto          rw,user,noauto  0       0

to

/dev/fd0        /media/floppy0  ext2,vfat    rw,user,noauto  0       0

These lines qualify both the types of mounting (MSDOS/VFAT and LINUX/EXT2) common the floppies. This complements the argued correction.

---

### Post by mad-man on 2005-11-16
I updated Hoary to Breezy using the repositories for Breezy in the etc/apt/sources.list and by following the directions that were given.
quite straitforward. Worked like a charm :)

Then I noticed the floppy udi problem. 

putting deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper main restricted
in the sources list. And upgrading to pmount 0.9.6-1 with synaptic makes the problem go away!

thanks alot!

---

### Post by Healey on 2005-11-30
Hi
I am having the same floppy disc problems but I cannot fix it !

I have added "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted" to the sources.list file but when I run Synaptic I get the following error 

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)


I KNOW i am doing something very wrong but I cannot work it out

I am very new at this as you can tell !!

I would be happy if anyone could help

Regards

Healey

---

### Post by hajk on 2005-11-30
The updated pmount-package has recently been put in the breezy-backports repository... this solves the floppy problem (it does for me).

---

### Post by Healey on 2005-11-30
Hi
Thanks for you reply

I found another thread :
[http://ubuntuforums.org/showthread.php?p=467554](http://ubuntuforums.org/showthread.php?p=467554)

And this fixed my problem - (I hope)

Thanks again for your time

Regards

Healey

---

### Post by Bullitt on 2005-11-30
[QUOTE=Healey]Hi
I am having the same floppy disc problems but I cannot fix it !

I have added "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted" to the sources.list file but when I run Synaptic I get the following error 

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)

[/QUOTE]

I've gone down this same road. Could someone explain where the updated pmount-package is located?

Thanks,
Hank

---

### Post by zlogic on 2005-12-01
An alternative way: go to [http://packages.ubuntu.com/breezy-backports/utils/pmount](http://packages.ubuntu.com/breezy-backports/utils/pmount)
and download the package manually, then install manually (dpkg -i some_file.deb).

---

### Post by jimw on 2005-12-03
Thank you all very much.  I'd been using Mandrake 10.0 for some time, and there seems to be easily accessible help on the Mandrake setup for everything.

I wouldn't be surprised if the help is there, just not in a place where I think to look for it.

My main use for the computer is in word-processing (I'm a writer) but I've picked up a bit about linux along the way.

One problem I have is that the "help" on the Disk Manager dialog is missing, and I'm told to "check my installation."  

Does this mean I should re-install, or is there some other sort of thing I could do?

Second question is, just how do I set things up so that files on the windows section of my dual-boot are accessible to me?

Further, there appears to be a large section of my hd that is inaccessible to me.

I cannot now seem to repeat the commands that brought me to the dialog that dealt with my hd and the various sections and their inaccessiblity.

If anyone can help a poor bewildered writer, I'd be grateful.

JimW

---

### Post by rplantz on 2005-12-03
In Synaptic, I can see that pmount 0.9.6-1 is in breezy-backports. (Select the package, then Properties, then the Versions tab.)

I added that repository about a week ago, and apparently update installed it for me.

I'm running xfce. I insert a floppy, and ROX automatically mounts and unmounts the floppy for me.

To test this, I copied a pdf file, unmounted and ejected the floppy. Then I inserted the floppy and could open the file from the floppy.

Seems to work quite well.

---

### Post by Stratuscaster on 2005-12-21
Admittedly, I'm a novice at Linux.

I've attempted to follow the directions here and in the other linked threads, but am stopped at a rather simple stage that I'm unable to figure out.

When attempting to edit the /etc/apt/sources.list file, I cannot. It's read-only.

I did delve further into resetting permissions, activating the root account, and CHOWN and CHMOD, but that ultimately screwed up my system - the Package Manager and other programs would no longer run.

I'm sure there is a simpler way to get this done, but I've yet to find it.

So how about some help for the new guy?

---

### Post by paddyg on 2005-12-21
when I wrote my post on Nov 3 ( post # 3 above) pmount 0.9.6-1 was only in dapper rep, but now it's in breezy backports ---as rplantz has pointed out.

No chown or chmod to edit sources.list---I don't think it's very wise to chown and chmod /etc...

In terminal, just type
```
sudo gedit /etc/apt/sources.list
```

then uncomment the following line:

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by Stratuscaster on 2005-12-21
Thanks. But I found the method that "makes sense" to me.

I can change the repositoties from within the Package Manager, and then simply choose pmount from the Package Manager.

---

### Post by GeneralZod on 2005-12-21
[QUOTE=Stratuscaster]
When attempting to edit the /etc/apt/sources.list file, I cannot. It's read-only.

I did delve further into resetting permissions, activating the root account, and CHOWN and CHMOD, but that ultimately screwed up my system - the Package Manager and other programs would no longer run.
[/QUOTE]

For future reference, if you want to edit a file owned by root:

```

sudo gedit /etc/apt/sources.list

```

The following is a helpful read:

[https://wiki.ubuntu.com//RootSudo](https://wiki.ubuntu.com//RootSudo)

---

