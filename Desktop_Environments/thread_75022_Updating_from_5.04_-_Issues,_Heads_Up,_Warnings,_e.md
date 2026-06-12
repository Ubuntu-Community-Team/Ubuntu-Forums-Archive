---
title: "Updating from 5.04 - Issues, Heads Up, Warnings, etc...?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by jsimmons on 2005-10-13
I'm currently using 5.04. Can I just "upgrade", or do I have to do a complete re-install?

Is there anything I should look out for as far as XOrg, Gnome, or other configurations?

Is there any impact of my current Wine install?

---

### Post by ykpaiha on 2005-10-13
I usualy prefer a fresh and clean install preserving a home on a separate partition.
mainly because it's a way to clean a bit my trials....:KS

---

### Post by izmaelis on 2005-10-13
I think it is better to do a clean install, but if you wish to dist-upgrade be smart and create backup for your current system.

---

### Post by MarcDM on 2005-10-13
I got to hoary by apt-get dist-upgrade from Warty. Even now, synaptic looks like the old Wary style. VMWare looks strange too, not like everything else. 

I think I also had to fix a couple of things by hand. I don't quite remember (so long, bout 6 months ago ;) )

what does that mean? Fresh install is my recommendation.:???:

---

### Post by rooster on 2005-10-13
@MarcDM: Thank you for your information! It will help me for the upgrade this weekend!

---

### Post by estel on 2005-10-13
I'm not in a rush, and d/ling is too much of a hassle, so I'm going to wait for ShipIt to arrive with some CDs before I do a reformat and install, making sure that I copy /home (I didn't make a separate partition for it) over to the windows partition as a backup.

---

### Post by Synt4x_3rr0r on 2005-10-13
I dist-upgraded and my Nvidia drivers freaked out.
Couldnt start X.

I was lucky to have a backup of my xorg.conf and when i replaced it with the backup, it worked like a charm :D

But 10 minutes ago i formatted the system anyway :P

---

### Post by YanH on 2005-10-13
I also had the same problem with the Nvidia drivers :( . It only occurred with the latest version of the kernel. My attempt to fix it totally wrecked X resulting in me having to do a complete reinstall to get it to work. So proceed with care!
With my new install everything, including the Nvidia drivers, is working beautifully :KS

---

### Post by InsomniacUK on 2005-10-13
[QUOTE=izmaelis]I think it is better to do a clean install, but if you wish to dist-upgrade be smart and create backup for your current system.[/QUOTE]

So true. I did not do this and just lost my entire installation. Just reinstalled using Breezy RC1 that I downloaded before.

---

### Post by Abiezer on 2005-10-13
Just complet a dist-upgrade from a reasonably fresh Hoary install and it's been fairly painless, though had to rereun pppoeconf and had some warning at login about configuration being wrong so default used which i'm searching for info on now
Was surprised to not be able to open a terminal on right click in breezy. Should have read more before upgrading! :)

---

### Post by ChrisTheGeek on 2005-10-13
I uninstalled the NVidia drivers, did an apt-get upgrade from Hoary->Breezy and it worked great (with the RC release).  I found that the new splash screen didn't show when booting up the PC but everything else was ok.

However, depending on how much rubbish you've installed you may prefer a clean start and a fresh re-install.  Remember to backup all the hidden folders in your home directory first!  Also, when you re-install make sure you have separate partitions for / and /home to make this easier in future.

Breezy is a stonkingly good release! :-D

---

### Post by stoneguy on 2005-10-13
[QUOTE=estel]I do a reformat and install, making sure that I copy /home (I didn't make a separate partition for it) over to the windows partition as a backup.[/QUOTE]

Uhhh, no. Copying your /home partition to NTFS is going to wipe all the ownership and permission info.

What you need to do is tar up the home directory, preserve that file across your reformat and reinstall, and then untar the file. Include the **p** parameter on the untar command to keep permissions identical.

If you haven't been there already, welcome to the command line ;)

---

### Post by yusufk on 2005-10-14
That seems like a good idea, but is it possible to create an additional partition and move /home to it if all the space has already been partitioned? And how will I inform future installs that the /home directory is on this existing partition?

---

### Post by Blob on 2005-10-14
Oh no....so a clean new install is the best way to go?

What about all the software that I have installed? Will I have to re-install? I guess I will have to re-configure everything?

How do I save my home directory? Just copy it to another drive and drop it back in after the install?

This seems much too painful and time consuming.

I think I will stick to hoary until I have a week to kill and do the upgrade.

---

### Post by Nevershine on 2005-10-14
[QUOTE=yusufk]That seems like a good idea, but is it possible to create an additional partition and move /home to it if all the space has already been partitioned? And how will I inform future installs that the /home directory is on this existing partition?[/QUOTE]

Look this:
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

I will try to move /home to another partition soon,because i 'd rather a clean instalation than a "apt-get dist-upgrade".

---

### Post by WorLord on 2005-10-14
Don't upgrade if you have an I2O based SCSI card and RAID.  The [kernel panics]("http://bugzilla.ubuntu.com/show_bug.cgi?id=16011").

(Anyone know where to get a newer kernel for Ubuntu?  Dapper?)

---

### Post by jasper_m on 2005-10-14
I tried dist-upgrade and it went horribly wrong... Luckily I had taken backups... Problems: It said that it can't use the LOCALE settings. Then it said that it also cant fall back to the default locale. Then it had some problems with kdevelop packages and the installation stopped at those packages... nothing worked, so after like 7 hours I had to do a fresh install...

---

### Post by Viper12 on 2005-10-14
Had the same problems.  did an apt-get clean and  ran it from the command line. rebooted into breezy after that, but I've got postfix issues and 7 other applications that got orphaned somehow.  EVerything works, but doing a dist-upgrade brings up the following:

Errors were encountered while processing:
 postfix
 mailx
 mutt
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Again, the system seems to be running just fine (no vid/sound or desktop issues so far), but that is worriesome nonetheless.

---

### Post by khu19 on 2005-10-14
I tried doing an apt upgrade last night and it went horribly wrong, bunch of errors upon bootup and X wouldn't start.  Decided it was best to format and do a clean install and had Breezy running within the hour.

For those who want an easy way to backup their /home/ to an existing windows partition, I used this neat program from windows:

[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm]("http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm")

Lets you read and export linux directories from Windows, very cool!

kev

---

### Post by stryderjzw on 2005-10-14
[QUOTE=Viper12]Had the same problems.  did an apt-get clean and  ran it from the command line. rebooted into breezy after that, but I've got postfix issues and 7 other applications that got orphaned somehow.  EVerything works, but doing a dist-upgrade brings up the following:

Errors were encountered while processing:
 postfix
 mailx
 mutt
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Again, the system seems to be running just fine (no vid/sound or desktop issues so far), but that is worriesome nonetheless.[/QUOTE]

I also did dist-upgrade and ran into some problems, but this is how i fixed postfix problem.

I first went to System/Administration/Services and disabled postfix by unchecking the box.  Then I reinstalled postfix through Synaptic.  This should work and resolve a few other software dependancies as well.  Then I reenabled Postfix in Services by rechecking the box.

Hope that helps.

---

### Post by astoltz on 2005-10-14
OK I have a related question but I haven't seen it covered anywhere.  If /home is on a separate partition, what happens when you get to the part in the installer about making new users?  You have to make identical user ids I assume, but is it as simple as that?  The install then sees that /home/user already exists and that's it - all the settings / data are preserved?

Just want to be sure.

---

### Post by Viper12 on 2005-10-14
[QUOTE=stryderjzw]I also did dist-upgrade and ran into some problems, but this is how i fixed postfix problem.

I first went to System/Administration/Services and disabled postfix by unchecking the box.  Then I reinstalled postfix through Synaptic.  This should work and resolve a few other software dependancies as well.  Then I reenabled Postfix in Services by rechecking the box.

Hope that helps.[/QUOTE]

You're my new hero.  that worked like a charm.  Thanks for the response!
:D

---

### Post by towsonu2003 on 2005-10-15
[QUOTE=astoltz]OK I have a related question but I haven't seen it covered anywhere.  If /home is on a separate partition, what happens when you get to the part in the installer about making new users?  You have to make identical user ids I assume, but is it as simple as that?  The install then sees that /home/user already exists and that's it - all the settings / data are preserved?

Just want to be sure.[/QUOTE]

Before logging in to gnome, you may want to go to a terminal ( CTRL+ALT+F1 ), login with your username and pass, and:

ls -l /home/username

check that you own the files (if you see numbers, you don't own them, read along; if you own them, see the end of this)

if you don't own the files: 

sudo chown -R username:username /home/username

This will restore the group and user ownirship. Everything (-R) under /home/username (it included) will be owned (chown) by you.

you may also want to do:

chmod -R 600 /home/username
chmod -R u+X /home/username

to employ strict permissions. 

after this, 

exit
CTRL + ALT + F7

Will take you back to the gnome login window. Just login.

IMPORTANT NOTE: Please wait for some time so that someone else can correct my errors, if any.

---

