---
title: "Unison"
date: 2008-10-14
forum: Desktop Environments
---

### Post by Quarkrad on 2008-10-14
Can anybody help a new Ubuntu user?  I have two hard disks in my PC - one will be a backup of user docs.  On hd1 I would like to create two folders:
Folder 1 for docs
Folder 2 for Photos

Ideally these would be on a different partition to where Ubuntu sits but I do not think Unison allows me to do this - so far it seems all I can select are local folders that sit under root (i.e. in the same partition where Ubuntu runs).

Now I would like to enter (into Unison) the remote folders that I want to sync with - i.e. my backup folders on hd2.   I cannot see, though Unison's screens, how you enter the path for hd2.  (In fact I cannot see how you would enter a path to a different partition on hd1).  In windows terms it would be something like:

c:\   Ubuntu     (on hd1)
d:\   folder 1 and folder 2   (on hd1)

e:\   Backup folder 1  (hd2)
f:\   Backup folder 2  (hd2)

I would like to sync

d:\folder 1 with e:\ folder 1
d:\folder 2 with f:\ folder 2

I have spend some hours on this but keep getting bogged down with Linux apps that do amazing complex things with remote PCs over networks.  I am struggling to find something simple that will keep a duplicate of my working folders on hd1 on hd2.  Unison has been suggested  but I cannot seem to drive it.  I can see other hd1 partitions in the 'Computer' window but so far not hd2.  Any help/advice appreciate.  (Note - I had this functionality via a small app on winxp called smartsync pro - it sync'd all folders on PC shutdown.

---

### Post by swisscow on 2008-10-14
Have you installed unison-gtk - that gives the graphical frontend from which you can navigate to your chosen folders.

Don't know about internal drives, my external is mounted in the media folder.

---

### Post by Quarkrad on 2008-10-14
thank yo - yes I did install this version.  I do have a graphical front end - struggling to find out how to 'point' to different partitions.

---

### Post by swisscow on 2008-10-14
try creating a new profile. Double click it, when the file picker comes up navigate to /      i.e. root. Should be able to access everything from there.

Got to go, cooking dinner

---

### Post by Mazin on 2008-10-14
It's not clear to me, but perhaps the confusion could be with the Unix filesystems.
Instead of having a different drive letter for every partition you have, each partition is mounted as a different directory underneath "/".  In other words, they will appear as regular directories somewhere inside your filesystem "/".

Usually, your other hard drive partitions will be under [FONT="Lucida Console"]/media/something[/FONT]

Or, you can right-click on the folder or drive on your desktop and see where it is (right-click&#8594;Properties&#8594;Volume tab&#8594;Mount point).

---

### Post by Quarkrad on 2008-10-14
Thank you all - getting a little clearer.  Yes I can see hd2 - as said all partitions and other HDs are visible under root.  I did have a look at Properties for two demo folders I set up on two different partitions.  They were both /media/xxx/folder name.

A little problem but I think I am on the way (at the moment Unison is telling me /media/xxx does not exist).  I will keep trying and let you know.

---

### Post by Quarkrad on 2008-10-14
OK - I've cracked the first part.  Managed to set up and sync two folders - many tans for all your help.  A couple of questions pls:

1.  Created another profile but made silly mistake - can't see how to edit. I can create yet another but how do you delete profiles or edit mistakes in others.

2.  Having set up a working profile (I went into the destination folder and saw new files in there) - what options are there to automate this/have it working in the background?  Do you have to kick the backup/sync process off manually - if so how do you do it?

---

### Post by Mazin on 2008-10-14
Hi.  Scheduling tasks is a fundamental feature of Linux and Unix-like operating systems.  Take a look at [Cron]("https://help.ubuntu.com/community/CronHowto").  For an easier, graphical setup for scheduling tasks, install "gnome-schedule" which provides a front-end to cron and at.

---

### Post by swisscow on 2008-10-15
[QUOTE=Quarkrad;5964660]OK - I've cracked the first part.  Managed to set up and sync two folders - many tans for all your help.  A couple of questions pls:

1.  Created another profile but made silly mistake - can't see how to edit. I can create yet another but how do you delete profiles or edit mistakes in others.


To do this, open up your home folder and show hidden files. There will be a folder in ther called .Unison . Go into that, you can see your profiles. Edit them with a text editor or delete them.

Glad it is working

---

### Post by Quarkrad on 2008-10-15
Sorry to keep asking questions.  I have set up Unison to sync the folders I need, installed Gnome Scheduled Tasks and read the Help file.  It looks OK to set up an automated schedule.  What I do not understand is the Command string I need to input in order to kick off the sync'ing.  Any help much apprecated - specific would be great but I feel I also need to read/understand these Command strings, how they work/what you enter etc.

Thanks.

---

### Post by Mazin on 2008-10-16
If you just specify the command "unison", it should start unison which will automatically  sync whatever is in your profile.

---

