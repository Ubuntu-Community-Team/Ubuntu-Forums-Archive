---
title: "Cannot mount floppy from Nautilus"
date: 2005-10-25
forum: Desktop Environments
---

### Post by dpm on 2005-10-25
Hi everyone,

I know this has been reported before and there is a workaround for it, but I have got an extra question. My computer is running Breezy from a fresh install and with everything up to date.

The problem is that I cannot mount the floppy disk drive from the 'Places'>'Computer' menu. When I use the 'Mount Volume' menu option, with the floppy inserted, I get the following error message:

Unable to mount the selected volume.
Error: given UDI is not a mountable volume

and the floppy drive is then obviously not mounted. The workaround for this is to use the command 'pmount -d /dev/fd0' from the terminal, and then everything works fine. I can even unmount the floppy drive by right-clicking on the icon.

Ok, that's all well, and although annoying, I am happy using the workaround if there isn't any other solution. However, I see that this same problem I am having is reported at [http://bugzilla.ubuntu.com/show_bug.cgi?id=17562]("http://bugzilla.ubuntu.com/show_bug.cgi?id=17562"), and marked as FIXED (more specifically, fixed upstream). My question then is:

where has that been fixed? I have installed the latest updates and I am still having the same problem!

Or does "fixed-upstream" mean that that has only been fixed for the next "Dapper" release. If that is so, will there not be a patch for Breezy?

As I said, I am happy with using the workaround, but it would be nice to know what is the current situation of this "feature".

Thanks.

---

### Post by canadianwriterman on 2005-10-25
I'd like to know what "fixed upstream" means, too. I'm using Breezy with a floppy launcher on my desktop that works fine, but the fix would be best, if I can get it.

---

### Post by dpm on 2005-10-25
Ok, after re-reading [http://bugzilla.ubuntu.com/show_bug.cgi?id=17562]("http://bugzilla.ubuntu.com/show_bug.cgi?id=17562"), I think I understand the following:

1) the problem is due to a bug in the pmount package

2) the bug has been fixed upstream, which means that it has been fixed for debian (is that correct?).

3) the current Breezy version of pmount is 0.9.5-0ubuntu5 (breezy). The new debian package is the same as the dapper package, with version 0.9.6-1.

4) there is currently no breezy version of the new package, or at least, not available from the official, multiverse or universe repositories.

If I am right in my assumptions (please correct me if I'm not), my questions are:

a) Did I get the meaning of "fixed upstream" right?

b) will there be a version of the fixed package for breezy, or will that only be applied to dapper?

c) if there is not going to be a breezy package, could I just get the 0.9.6-1 debian package and upgrade my local package manually? Could anyone give any pointers on how to do this without breaking my system?

I am fairly new to linux and ubuntu (although I have been using hoary and breezy for a while now), so any comment will be greatly appreciated.

---

### Post by dpm on 2005-10-25
Following what I read at [http://bugzilla.ubuntu.com/show_bug.cgi?id=17607#c33]("http://bugzilla.ubuntu.com/show_bug.cgi?id=17607#c33"), in relationship to this bug: [http://bugzilla.ubuntu.com/show_bug.cgi?id=17562]("http://bugzilla.ubuntu.com/show_bug.cgi?id=17562"), I installed the fixed pmount package:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.6-1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.6-1_i386.deb")

with 

sudo dpkg -i pmount_0.9.6-1_i386.deb

and so far it seems to be working for me. I can now mount/unmount the floppy from Nautilus with no problem :D!!! Please note that the package seems to be for dapper and not breezy (read the links carefully), but it installed fine on my system and seems to be running with no problems.

Maybe there is going to be a package for breezy, I don't know. The package seems to be quite recent (uploaded today), and as long as I don't detect any problems, I will keep using it (if necessary, I can always go back to the original version that comes with breezy).

P.S. if anyone is still interested, I found out that "upstream" refers to the core developer/s of the software, whereas the maintainer or debian developer is in charge of maintaining the .deb package apppropriate for each release. It can also be that the upstream developer and debian developer are the same person.

---

### Post by canadianwriterman on 2005-10-26
[QUOTE=desp]Following what I read at [http://bugzilla.ubuntu.com/show_bug.cgi?id=17607#c33]("http://bugzilla.ubuntu.com/show_bug.cgi?id=17607#c33"), in relationship to this bug: [http://bugzilla.ubuntu.com/show_bug.cgi?id=17562]("http://bugzilla.ubuntu.com/show_bug.cgi?id=17562"), I installed the fixed pmount package:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.6-1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.6-1_i386.deb")

with 

sudo dpkg -i pmount_0.9.6-1_i386.deb

[/QUOTE]

Bump

Is that URL a repository? I can't get it to stick as a repository in Synaptic (ie. nothing happens when I "add" it to the repositories through Synaptic... it dowsn't show up on the repository list) and I get this error just running it through apt-get:

stephen@Home:~$ sudo dpkg -i pmount_0.9.6-1_i386.deb
dpkg: error processing pmount_0.9.6-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 pmount_0.9.6-1_i386.deb
stephen@Home:~$

---

### Post by dbet on 2005-10-26
You dont need to add it to your repository. Just click on the link and save the download to your folder. After you have saved the file, open a terminal and cd to the folder where you saved the file and install the package 


with


sudo dpkg -i pmount_0.9.6-1_i386.deb


P.S. DO NOT UNINSTALL THE PRIVIOUS VERSION OF "pmount"

After I installed the package, everything works like it is supposed to.

---

### Post by canadianwriterman on 2005-10-26
Thanks, that worked great and now I can mount from Nautilus! It did seem to replace the current version, which I assume it was supposed to.

---

### Post by dpm on 2005-10-27
dbet, canadianwriterman: glad to hear this worked for you, too.

---

### Post by bluemuffin on 2005-10-28
Hello

I have the same problem with my floppy. I recently installed breezy and the following error returs when i try to mount a floppy:

[COLOR="Red"]Error: given UDI is not a mountable volume[/COLOR]

I tried the work around command: [COLOR="Blue"]pmount -d /dev/fd0[/COLOR] but my floppy still does not mount (same error is returned).

So, i downloaded pmount_0.9.6-1_i386.deb and put it in my home folder (i can't still figure out how /home/folder1/folder2 works so i put everything in the home folder). Even downloaded it twice and copied it to the Home folder twice to be sure about it.

So I CD into the home folder and the terminal looks like this:

[COLOR="Blue"]redone@RED-ONE:/home$[/COLOR]

Then:

[COLOR="Blue"]redone@RED-ONE:/home$ sudo dpkg -i pmount_0.9.6-1_i386.deb[/COLOR]

after I typed the command.

The following error resulted:

[COLOR="Red"]dpkg: error processing pmount_0.9.6-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 pmount_0.9.6-1_i386.deb[/COLOR]

I did the whole process (from copying the debian package to home and then executing dpkg) twice but there was still the error.

Is there something I have missed? Or maybe some other way to mount my floppy?

Thanks a lot guys. I'm learning Linux, albeit at a snail's pace (gee, i'm not basically a logic and numbers man), because of this forum.

;) 

BTW, I have installed breezy on another computer and it encountered the same problem.

---

### Post by HJThis on 2005-10-28
Hello,bluemuffin & Welcome

Open a Terminal & do this here

sudo dpkg -i pmount_0.9.6-1_i386.deb

you may need to use password

it always works for me

Best of luck:D

i would also like to add if i may have a look at this great like
this Thread started by **Kyral** it has been a big help to me
[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)

---

### Post by arazaxirelcinellersadolur on 2005-11-14
hi,
:confused: 
but i wonder why this solved problem-matter does not putted for installing via Update ???
:rolleyes:

---

### Post by ph0x on 2005-12-11
Hello everyone!
I also installed the new version of pmount on my ubuntu breezy-system.
But it says: Unable to execute pmount
With sudo there are no problems executing it. When I type "pmount" in my console as user it says me:
```
bash: /usr/bin/pmount: No rights
```
Do I lack the rights for executing pmount or what else could that be?

/etc/fstab:
```

proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda8       /daten          vfat    gid=1000,uid=1000 0       0
/dev/hda9       /home           ext3    defaults        0       2
/dev/hda7       /root           ext3    defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

I am member of groups "floppy" and "cdrom".


greetz ph0x

---

### Post by canadianwriterman on 2005-12-11
Did you install the bug-fix for pmount?

To update pmount, go to:

**[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)**

Download and install **pmount_0.9.6-1_i386.deb**

Note that there is another pmount file with the Breezy name in it. That file did not work for me... I used the one I've noted above and it works fine.

Also, in you fstab file, add **vfat** to your floppy line like:

**/dev/fd0        /media/floppy0  auto,vfat    rw,user,noauto  0       0**

---

### Post by ph0x on 2005-12-11
Yes, I did install the bug-fix version.
Editing my /etc/fstab did not change anything.
But nautilus doesn't even come to the point where it could mount the floppy. Bash says that I don't have enought rights to use pmount.
Do I have to join a special group to use pmount? With adm, admin and root it didn't work so far...


greetz ph0x

---

### Post by ph0x on 2005-12-13
Well, after some time of research I found that:

- Your user has to be a member of group plugdev
- The 0.9.6-1~breezy package can also handle the automount correctly (you can even get it by apt-get)


greetz ph0x

---

