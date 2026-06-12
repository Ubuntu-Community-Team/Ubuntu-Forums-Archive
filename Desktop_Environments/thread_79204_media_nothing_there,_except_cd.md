---
title: "media:/ nothing there, except cd"
date: 2005-10-19
forum: Desktop Environments
---

### Post by stoeptegel on 2005-10-19
I just installed myself 5.10, and saw none of my disks listed in media:/.
What i like to know is, 

Is this a known bug? Are there more people having this issue? Or is it my bad install skills?

Thanks.

---

### Post by OldGaf on 2005-10-19
I upgraded a few days ago...... everything was fine. Then upgraded again today, now all I have in my Media:/ is my diskette drive!

---

### Post by dr_kabuto on 2005-10-20
I've opened a bug for this: [http://bugzilla.ubuntu.com/show_bug.cgi?id=18169]("http://bugzilla.ubuntu.com/show_bug.cgi?id=18169")

---

### Post by jeremy on 2005-10-20
I had been going to submit the bug but you beat me to it. I have added a comment to yours.

---

### Post by Craig Prevallet on 2005-10-20
Same here.

---

### Post by stoeptegel on 2005-10-20
Thanks for the bug report. :KS 

At my desktop media:/ is listing the dvd/cd instead of a floppy though. My floppy station is broken and disconnected, maybe that has something to do with the difference.

---

### Post by OldGaf on 2005-10-20
Hmmmm......      Status is resolved ?

---

### Post by stoeptegel on 2005-10-20
Well, that wasn't me... we might want to add a link to this thread too.

---

### Post by jeremy on 2005-10-21
I have reported it as a new bug at [http://bugzilla.ubuntu.com/show_bug.cgi?id=18211](http://bugzilla.ubuntu.com/show_bug.cgi?id=18211)

---

### Post by RSX311 on 2005-10-21
Yeah, same thing happens to me, I mounted a  FAT32 partition and a NTFS partition and they don't show up under Storage Media.  I have to go to System -> Disks to access the partitions or go through Konsole.

---

### Post by Craig Prevallet on 2005-10-21
[QUOTE=jeremy]I have reported it as a new bug at [http://bugzilla.ubuntu.com/show_bug.cgi?id=18211](http://bugzilla.ubuntu.com/show_bug.cgi?id=18211)[/QUOTE]
Downgrading to kdebase 4:3.4.3-0ubuntu4 and kdebase-kio-plugins 4:3.4.3-0ubuntu4 allowed me to get media:/ working again for me.  Hope this gets fixed quickly.

---

### Post by oobuntoo on 2005-10-28
Downgrading to kdebase 4:3.4.3-0ubuntu4 and kdebase-kio-plugins 4:3.4.3-0ubuntu4 solves one problem but creates another if you use fat32. KDE program like kaffeine will not open files that are on fat32. It tells you that remote files are not accepted, only local files. Same thing happen if you want to use a file on fat32 as your wallpaper. But if you browse to the locations of these files and double click on them, they will open and play just fine, even  with Kaffeine. This happens only with KDE apps, even if you are root. 
The more serious problem is that Adept, and even Synaptic, cannot install anything from cd. You can mount cd, but as soon as Adept tries to install a package from cd, the cd-rom drive get unmounted.

---

### Post by stoeptegel on 2005-11-02
Problem is solved for me since i installed a fresh kubuntu. (apt-get update & upgrade also done)

---

### Post by Princey on 2005-11-02
[QUOTE=stoeptegel]Problem is solved for me since i installed a fresh kubuntu. (apt-get update & upgrade also done)[/QUOTE]

Strange, I did a fresh install yesterday morning and I don't see my mounted NTFS and FAT32 drives. I have to mount them and link to folders for me to access them or as one person earlier noted, I have to go through the system settings and drives to access them.

---

### Post by stoeptegel on 2005-11-02
But indeed after a reboot the problem is back, lol. This one really must be solved cause you get lots of irritating popup errors of it. (i.e. loading a dvd movie)

---

### Post by jeremy on 2005-11-03
Please, everyone confirm the bug at [http://bugzilla.ubuntu.com/show_bug.cgi?id=18211](http://bugzilla.ubuntu.com/show_bug.cgi?id=18211)
hopefully we'll get it fixed soon.

---

### Post by stoeptegel on 2005-11-07
Bug is still not accepted...   I am thinking heavily of reverting back to hoary since this bug comes back in many programmes that use the media:/ kioslave.

---

### Post by OldGaf on 2005-11-07
What will it take to get this fixed??? I don't want to go back to Hoary, but this is a big bug!

---

### Post by sdr_ar on 2005-11-08
I found a temporary (I guess) solution. 
I uncommented the last line of /etc/default/hal

This is the result:

# This will run the hal daemon as normal user 'hal' with some additional
# privileges; This will not execute callout scripts as root (so fstab-sync
# won't work) and makes hal unable to do filesystem type autodetection for
# non-removable devices.
DAEMON_OPTS=

# This will run the hal daemon as user root 
DAEMON_OPTS=--retain-privileges

---

### Post by f1dave on 2005-11-08
Well, wait a second...

Do we actually know that media:/ should display hard disks? I mean, is it just for removeable media perhaps, like CDs, usb sticks, DVDs, etc? Just a thought of course.

---

### Post by sdr_ar on 2005-11-08
Yes, Media Storage shows all the media (removable or not) that you have to store data. The first time that I installed Kubuntu, it was showing all the partitions of my HD, then when I have updated the system it stopped working well, it was just showing the floppy. Now, with that modification in /etc/default/halt I can see all again. USB works well, CD's, DVD's. I dont't know if that is the optimum solution, but for now, it is simply a solution.
If somebody considers that it is not good for the system (i.e. if it is dangerous) please tell me.
Regards.

---

### Post by rjwood on 2005-11-09
[quote=sdr_ar]I found a temporary (I guess) solution. 
I uncommented the last line of /etc/default/hal

This is the result:

# This will run the hal daemon as normal user 'hal' with some additional
# privileges; This will not execute callout scripts as root (so fstab-sync
# won't work) and makes hal unable to do filesystem type autodetection for
# non-removable devices.
DAEMON_OPTS=

# This will run the hal daemon as user root 
DAEMON_OPTS=--retain-privileges[/quote]

Thanks- I 've been going crazy with this all morning. is dragging and dropping the only way to get files onto a floppy. Open Office doesn't let me save to floppy. Any help is appreciated.

---

### Post by sdr_ar on 2005-11-09
I would need more details. What Does OpenOffice tell you? Any Message... Or something

---

### Post by rjwood on 2005-11-10
[quote=sdr_ar]I would need more details. What Does OpenOffice tell you? Any Message... Or something[/quote] 
Hi sdr_ar--Thanks for responding. I figured it out. My daughter needs this for school papers, she saves them on floppy's. Anyway I figured out that she just needs to use the copy option after saving her work and pasting it onto the floppy, or she can drag and drop. thanks again..

btw in case you want the permanent solution see this thread:
[http://www.ubuntuforums.org/showthread.php?t=78986&page=2]("http://www.ubuntuforums.org/showthread.php?t=78986&page=2")

---

### Post by OldGaf on 2005-11-23
> I found a temporary (I guess) solution.
I uncommented the last line of /etc/default/hal

This is the result:

# This will run the hal daemon as normal user 'hal' with some additional
# privileges; This will not execute callout scripts as root (so fstab-sync
# won't work) and makes hal unable to do filesystem type autodetection for
# non-removable devices.
DAEMON_OPTS=

# This will run the hal daemon as user root
DAEMON_OPTS=--retain-privileges
Attached Files:

Thanks for the work around. Was driving me nuts!

---

### Post by the_it on 2005-11-23
Quick fixes:

entries in fstab automatically become media:/ entries.  So if you edit your fstab using your favorite means to add the folders, then you get to have them pop up.

---

### Post by sdr_ar on 2005-11-24
How would you change the fstab? Could you give me an example?

---

### Post by vitorsouza on 2005-11-24
[QUOTE=stoeptegel]I just installed myself 5.10, and saw none of my disks listed in media:/.
What i like to know is, 

Is this a known bug? Are there more people having this issue? Or is it my bad install skills?

Thanks.[/QUOTE]
I noticed a similar problem here. On Kubuntu 5.04 the HD partitions used to show at media:/ and now, with 5.10, they disappeared. That's alright for me, since they're mapped on fstab to the appropriate directories in the file system.

The problem is that my USB drive stopped working and I thought it was a related problem. Then I noticed that the module usb_storage wasn't loaded (don't know why). Once I loaded it, my USB drive worked again.

CDs and DVDs also get detected and open fine. I don't have a diskette drive in my notebook, so I can't say.

Hope this helps someone...

---

### Post by ScoobyDan on 2005-12-01
> **sdr_ar]I found a temporary (I guess) solution. 
I uncommented the last line of /etc/default/hal

This is the result:

# This will run the hal daemon as normal user 'hal' with some additional
# privileges said:**
> 

I tried this fix, which has solved the problem of none of my harddrives appearing in /media/, but I still get this error when inserting a DVD-R into my DVD-RW:
[QUOTE]
An error occurred while loading media:/hdc:
The file or folder media:/hdc does not exist.

I am running Ubuntu Breezy, with apt-get'd kubuntu-desktop and edubuntu-desktop packages.

Any bright ideas? At the moment I am unable to burn anything to DVD, unless I log out and go back to GNOME (which confuses my wife no end!)

Many thanks

Daniel

---

### Post by GoldBuggie on 2005-12-01
You could do a
```
sudo mkdir /media/hdc
```
then setting some privilieges
```
sudo chmod +777 /media/hdc
```
Now try again. Hope it works out for ya.

---

### Post by ScoobyDan on 2005-12-01
Hi,

I tried your suggestion, but it hasn't worked. I think it is because the error is
> 
media**:**/hdc
not
> 
media/hdc

Anyone else with any suggestions?

Daniel

---

### Post by GoldBuggie on 2005-12-01
Strange...I had that problem some time before and just creating the directory it referd to solved the problem. (I'm guessing you meant /media/hdc not media/hdc)

You could always add the correct entry for fstab, for dvd's, and make it refer to another directory.

---

### Post by roach of discord on 2005-12-28
Was this ever fixed?  I just installed kubuntu..upgraded, and got this issue.  Media:/  = only floppy.  Even though all my drives are in my fstab.

---

### Post by Konge Odin on 2005-12-29
I have the   problem still so I guess it is not fixed. Someone should really look into this fast. Everything here is working great exept that the fat 32  drives and the usb Zen    Nano plus mp3 player  wont show up in the Media window of the konqueror.

A workaround is to rightclick on the desktop and add shortcuts to all the missing volumes so that they show on the desktop  all the time.  
:)

---

### Post by stoeptegel on 2005-12-30
I don't want to complain cause it's free and open and all, but this really is something... :(

---

### Post by Konge Odin on 2005-12-30
Just has to mention that I run Neverwinter nights Platinum edition, Doom3 + ext and Quake4 without any trouble. They work better than in windows too. So to me it is quite clear that under the hood everything is working great, it is just not showing. The only problem with this is that it will scare off new users of Kubuntu, and so the community will get smaller. Hope it is easy to fix the problem of partitions not showing up in Media:/ .

---

### Post by whitesox on 2005-12-31
im sorry, have any of you thought to look in /media ?
media:/, as far as i know, is indeed reserved for temporary storage
I remember that in hoary I managed to change that, but as of now I only have 1 partition, so there is no way for me to check if any way works, but i think I have one:
right click on the desktop > configure desktop > behavior > device icons > check the box mounted hard disk volume
it should show up on the desktop anyway
if you have permisson problems, use the mounting tool in system settings
but let me repeat: **CHECK /media/**

---

### Post by fig_jam_uk on 2006-01-01
If you just need to access the dives but know the mounpoints, (im having same problem) open the media folder where you only get the cd or floppy drives and remove everything from the address bar and just put a / and it will give you the root drive, Hope this helps a bit :rolleyes:

---

### Post by whitesox on 2006-01-01
allright, it seems that no one else gets this.
media:/ is a special address, used only by konqueror, that displays removable media.
If you want to get to your actual partitions, this is what you do:

Go to /etc/fstab

it should look something like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1      /media/hdb1   ntfs  defaults,uid=1000,gid=1000,auto,rw,nouser 0 0
/dev/hdb2      /media/hdb2   ntfs  defaults,uid=1000,gid=1000,auto,rw,nouser 0 0
/dev/hdb3      /media/hdb3   ntfs  defaults,uid=1000,gid=1000,auto,rw,nouser 0 0
/dev/hdb5      /media/hdb5   ntfs  defaults,uid=1000,gid=1000,auto,rw,nouser 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
As you can see, even though my partitions do not show up in media:/, they still exist in the /media/ folder, which is where they are mounted.  Try this, open up konqueror, and type in /media/, and see what shows up.  it really should be as simple as this, if not, enter this in at the terminal:
```
sudo mount -a
```
if no errors show up, check again.  If they still don't exist in /media/, then open up /etc/fstab
```
nano /etc/fstab
```
and move down to where the partition is located, and check to see where it it mounted, then copy that location into konqueror, and you should have access to your partition.

I am not sure how to get the partitions to appear in media:/, but they still exist, and should be mounted somewhere, so here are some useful commands on how to manipulate the partitions:
```
sudo mount -a
sudo mount /dev/hd<something>
sudo umount -a
sudo umount /dev/hd<something>

```
these mount and unmount the partitions, in /dev/hd<something>, the something is usually 'a' or 'b', followed by 1 and up, ex. /dev/hdb5, which is one of my windows partitions.

to edit fstab, there are many ways, but the easyest is:
```
sudo cp /etc/fstab /etc/fstab.bak
sudo nano /etc/fstab
```
ctrl-o and enter saves, and ctrl-x quits
be careful though, even though the first line backs up fstab, remember that fstab is very delicate, and if  you mess up anything, remember:```
sudo cp /etc/fstab.bak /etc/fstab
```
will restore it to its backed up state.


hope this helped to clear up the issue

---

### Post by stoeptegel on 2006-01-02
[QUOTE=whitesox]
hope this helped to clear up the issue[/QUOTE]

Nope i am sorry, but i already knew that. The problem is a broken basic kde functionallity, and some programs which using the media:/ kio_slave will brake when you can't set /media/hd** manual somewhere in the program. But thanks for trying making it a lighter issue for us. :)

I hope my english is well enough :rolleyes:

---

### Post by xristos on 2006-01-15
This worked for me 
[http://www.ubuntuforums.org/showpost.php?p=645412&postcount=20](http://www.ubuntuforums.org/showpost.php?p=645412&postcount=20)

:) :) :)

---

### Post by stoeptegel on 2006-01-15
Thank you thank you thank you xristos!  Finally a solution that works for me. :D (i have now access to my NTFS partition again too :) )

---

### Post by Kadin2048 on 2006-03-26
[QUOTE=xristos]This worked for me 
[http://www.ubuntuforums.org/showpost.php?p=645412&postcount=20](http://www.ubuntuforums.org/showpost.php?p=645412&postcount=20)

:) :) :)[/QUOTE]

I am having the same issue right now (when I insert a CD, a Konqueror window pops up and says "An error occurred while loading media:/hdc: The file or folder media:/hdc does not exist." However if I browse to /media, it's there) and so far none of the posted solutions have seemed to help any.

I have tried adding the "hal" user to group "disk," and also restarting the hotplug subsystem (sudo /etc/init.d/hotplug restart). I still get the "Error while loading media" error any time I insert a CD, and in order to eject it I have to go through the terminal and do a sudo umount /dev/cdrom.

I'm running KDE 3.5 on top of Ubuntu Breezy with the kde-desktop package installed, nothing particularly exotic.

My fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


In Konqueror, "media:/" displays two things, one is my flopply, another is "38G Media" which displays my root filesystem. The CD-Rom isn't listed there at all, regardless of whether it's mounted or not.

The "/media/" directory on the other hand, had cdrom, cdrom0, floppy, and floppy0. floppy and cdrom are both symlinks to floppy0 and cdrom0, respectively.

It seems like it's not the automounting feature that's broken per se, it's something in KDE...? Anyone have any other solutions to try?

---

