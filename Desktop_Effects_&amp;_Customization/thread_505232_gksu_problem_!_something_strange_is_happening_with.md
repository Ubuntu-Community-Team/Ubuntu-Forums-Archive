---
title: "gksu problem ! something strange is happening with root password"
date: 2007-07-20
forum: Desktop Effects &amp; Customization
---

### Post by vl.pavlov on 2007-07-20
hello 2 all

i got prob with gksu and root password

i set the owner of thunderbird (email) to be root, and to have all the perrmissions, and everybody else have no perrmisions at all, also i created launcher (shortcut) on desktop to the thunderbird as follows:

[ when i log in ubuntu linux (gnome) as a normal user (not root) ]

gksu /home/xyzt/install/thunderbird/thunderbird

and when i start it i can not pass with root password at all, and i can pass with normal user password?!

when i start the same launcher modified like this : (without gksu)

/home/xyzt/install/thunderbird/thunderbird

i can not acces because > Permission denied <, and that is ok]


is there a way to solve this?

why i am asked for user password when using file that only root can access?

thanx

---

### Post by hyperair on 2007-07-20
Well if I'm not mistaken, gksu is a GTK front-end to "sudo", and all admin accounts are allowed to use "sudo". What sudo does is that it takes the admin's password as a confirmation that that is the admin who is doing stuff to the computer, and then it executes whatever the command as the root user, hence granting temporary superuser access to your system. Hence, sudo works without the need for a root password. 

Take a look at this one: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by vl.pavlov on 2007-07-20
thanx 4 your reply

i tried with managing user  and when i uncheck "administrator of the sys" user can not run thunderbird with gksu

so my question would be more adequate like this:

how 1 can set the privileges to one executable file so that when normal user runs the application (with gksu or anything else) to be asked for the root password  ?

// like 1 is asked for his password in the variant i described in the start

?

---

### Post by vl.pavlov on 2007-07-20
or may b:

is there a way that root starts his application in gnome when normal user is logged (with root password) and if that user is not "administrator of the sys"

?

[ i am pretty new to all this stuff so sorry if somthing is not well formulated ]

---

### Post by hyperair on 2007-07-20
Please post the output of ```
stat /home/xyzt/install/thunderbird/thunderbird
```. I need to see it, before giving you appropriate instructions. Also, why is Thunderbird installed in your home directory? Shouldn't you use the one in the repository? Like...
```
sudo apt-get install thunderbird
``` or installing the thunderbird package in Synaptic Package Manager. Also, since you're new, I'd advise you to do this: whenever you go to get a certain piece of software, always look for .deb files, those are the ones used for Ubuntu. To install them you just double click on them, unless you're using Kubuntu.

Also, sorry I was mistaken earlier. Gksu is a front end to su, which logs in as the root user with the root password. The fact that you could use your own password with gksu means that the root account has the same password as your user.

Instead of gksu, use gksudo. gksudo is a front end to sudo and it works exactly as how I described above.

---

### Post by vl.pavlov on 2007-07-20
hello once more


stat /home/xyzt/install/thunderbird/thunderbird
pasted:

***

  File: `/home/xyzt/install/thunderbird/thunderbird'
  Size: 5205            Blocks: 16         IO Block: 4096   regular file
Device: 301h/769d       Inode: 4186883     Links: 1
Access: (0700/-rwx------)  Uid: (    0/    root)   Gid: ( 1000/  xyzt)
Access: 2007-07-20 14:32:04.000000000 +0200
Modify: 2007-06-04 20:31:51.000000000 +0200
Change: 2007-07-19 12:58:44.000000000 +0200

***


i have not used thunderbird from the repository because i also got it in the windows and both of them use the same profile on the independent partition (ntfs with 3g) so i needed 2.0.0.4 version of the thunderbird which is not in the repository yet (all my add-ons enigmail and so on use that version)




ls 
pasted:

-rwx------ 1 root   xyzt     5205 2007-06-04 20:31 thunderbird

(root is owner of the file, and others have no rights - as far i know) B)

... with gksudo i am asked for xyzt's password (that pass is different from root's)

---

