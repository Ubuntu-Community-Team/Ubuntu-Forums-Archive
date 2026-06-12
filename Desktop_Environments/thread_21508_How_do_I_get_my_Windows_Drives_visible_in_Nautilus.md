---
title: "How do I get my Windows Drives visible in Nautilus' &quot;Computer&quot; icon, like in Warty???"
date: 2005-03-22
forum: Desktop Environments
---

### Post by wernst on 2005-03-22
All,

OK, so after following the unoffical Warty guide, my 3 windows parititons would automatically display in the "Computer" icon on my Warty desktop. After upgrading to Hoary yesterday, they don't appear there anymore. They were all mounted in the /media/XXX type way, and I can still navigate to them this way. 

I've also used Symlinks to the /media/XXX structures, and I can access my files on those partitions that way too.

File Manager programs like Tux Commander still see the Windows partitions as mounted partitions in Hoary, so I know that they are corectly mounted and setup for access.

BUT, what I really want is for those parititons to appear as drives in the Nautilus "Computer" icon, or on the Hoary desktop, in the same way that it worked in Warty.

So, what's the problem, and how can I fix it?

Thanks,
Warr

---

### Post by bored2k on 2005-03-22
Same "problem" here .

On warty once I mounted the drives nautilus would pop up, and a desktop icon would appear.

Hoary does nothing .

---

### Post by Steel3 on 2005-03-22
I had this same exact problem, but after I did a dist-upgrade today all of the icons just showed up (including in the "places" menu as well).  You might want to try upgrading your system again.

---

### Post by Julius on 2005-03-22
The same happends to me, as I state in this post:
[http://ubuntuforums.org/showthread.php?t=20206](http://ubuntuforums.org/showthread.php?t=20206)

Sometimes after upgrading, the partition is shown, but it 'vanishes' after rebooting/restarting session.
I know it works, and I have no problem accessing to it via /media/XXX

Adding 'user' to fstab (as explained in the post mentioned above) helps: but it won't work the same. The partition will be shown as "xGB media", and I had troubles exploring the files on that partition.

What I want is that partition to appear in the "Places" menu, on my desktop, and in "computer:///".

---

### Post by wernst on 2005-03-22
OK, this is weird.

I was just about to upgrade th distro via apt-get when I just checked the "Comptuer" icon again.

And there are my mounted drives!

I don't understand it...


EDIT 1:

And now I rebooted and they're gone again. I'll try an update and see what happens.

EDIT 2:

OK, I did the update (boy it sure got a lot even after just 2 days of existance on my computer) and there's no change.

-warr

---

### Post by Julius on 2005-03-22
Lucky you, I still can't see my windows partition :(

---

### Post by Julius on 2005-03-22
Did a little research.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=7641](https://bugzilla.ubuntu.com/show_bug.cgi?id=7641)

Still don't know how to solve it xD

---

### Post by wernst on 2005-03-22
Well, I read that buglist entry too.

It seems that a new version of hal should fix it, (I guess). At lease someone knows about it.

I am currently running the version referenced in the last comment (0.4.7-1-13) and still have the problem...

-Warr

---

### Post by Steel3 on 2005-03-23
Wierd, happens to me too now -- everything's mounted fine in /media and a lot of applications can see them, so its all good.  Read the Bugzilla report, hopefully this'll be resolved soon.

---

### Post by Buffalo Soldier on 2005-03-23
[QUOTE=Julius]What I want is that partition to appear in the "Places" menu, on my desktop, and in "computer:///".[/QUOTE]For the *Places* menu: Does this method works for you? [http://ubuntuforums.org/showthread.php?t=21274](http://ubuntuforums.org/showthread.php?t=21274)

---

### Post by Shutdownrunner on 2005-03-23
You just have to edit the file /etc/fstab as root and in options column add "user". I don't know if it's the best method to solve this issue,but it works for me. An example:
/dev/hda1	/winc		vfat	user,defaults	0	0
And this way my windows partition is visible both on desktop and in computer:///.

---

### Post by Foden on 2005-03-24
It's this easy?

Thanks heaps!

---

### Post by c_dog on 2005-03-24
Check under "user and groups" in the system administration menu and make sure 'hal' in a member of the disk group. For some reason his (or its) group rights disappeared a couple weeks ago during a hal update. Hal still doesn't always reinitalize properly on a session restart, but at least it's not giving double icons for devices mounted by it (like say DVDs) and fstab at boot anymore. A reboot will bring the fstab desktop mounts back that are lost during a xsession restart.

---

### Post by wernst on 2005-03-24
Well, I added Hal to the Disk group. Restarted the computer as well as the Gnome session a few times.

Still no joy; it doesn't display Windows shares...

-Warr

---

### Post by wernst on 2005-03-28
I guess there's been no movement on this issue? The bugzilla discussion seems to have hit a brick wall...

-Warr

---

### Post by dodger on 2005-03-29
I found out that restarting dbus-1 with 

/etc/init.d/dbus-1 restart

causes all my partitons to show up in "Computer".
I'll try to play around with the script a bit and will post the results.

---

### Post by Julius on 2005-03-29
I remember the other day when I ran the updates, only a few packages were upgraded, and the windows partition showed up in my desktop after that. 
One of those few packages was dbus or related, I think, so I guess that's the one that has to be restarted in order to get partition shown :P

GOod work!!!

---

### Post by wernst on 2005-03-29
Excellent catch!!!

I too remember that after an update, I had visible partitions for a single session, but that was it. I just never made the connection, or I just wasn't observant enough...

-Warr

---

### Post by somuchfortheafter on 2005-03-29
i just edit my fstab and then create a link to my /windows directory on my deskop, windows is automatically mounted at startup for me so i dont worry about it to much, fstab entry is
:/dev/hda1       /windows        ntfs    defaults,ro,user,uid=1000       0 0

also this is required

$ sudo mkdir /windows

---

### Post by Shaggy on 2005-03-29
Great job Dodger, just restarted dbus and now my partitions are showing up like they should.

---

### Post by Nano on 2005-03-30
[QUOTE=Shaggy]Great job Dodger, just restarted dbus and now my partitions are showing up like they should.[/QUOTE]
 Also here.
It works

---

### Post by wernst on 2005-04-05
It seems this bug is still open.

I assume that everyone has to restart the dbus on every session in order to get their drives visible, right?

-Warr

---

### Post by Julius on 2005-04-05
[QUOTE=wernst]It seems this bug is still open.

I assume that everyone has to restart the dbus on every session in order to get their drives visible, right?

-Warr[/QUOTE]

Yup, the bug has not been solved yet :( I guess if it still happends on fresh installs. Hoary final is coming tomorrow I hope it get fixed.

---

### Post by didit on 2005-04-05
[QUOTE=Julius]Yup, the bug has not been solved yet :( I guess if it still happends on fresh installs. Hoary final is coming tomorrow I hope it get fixed.[/QUOTE]
 i have a tricky way to show up windows drivers on your desktop in Hoary. What you can do is that
remove '/' in front of dev of your windows partition. For instance in my case:

dev/hda1 /mnt/winC 		vfat    auto,user,exec,umask=000 0 0
dev/hda2 /mnt/winD 		vfat    auto,user,exec,umask=000 0 0

with this trick then you will always have windows drives visible in Nautilus also on your desktop.
Hope this trick can help you

ps. new comer here... :)

---

### Post by stepper on 2005-04-05
[QUOTE=didit]i have a tricky way to show up windows drivers on your desktop in Hoary. What you can do is that
remove '/' in front of dev of your windows partition. For instance in my case:

dev/hda1 /mnt/winC 		vfat    auto,user,exec,umask=000 0 0
dev/hda2 /mnt/winD 		vfat    auto,user,exec,umask=000 0 0

with this trick then you will always have windows drives visible in Nautilus also on your desktop.
Hope this trick can help you

ps. new comer here... :)[/QUOTE]
Thanks that did the job!! :smile:

---

### Post by didit on 2005-04-05
Glad to hear that the trick can solve your the problem. I found it by mistake..
Sometimes, it is worth to play with your system and make some mistakes   ;) 

-dyy

---

### Post by wernst on 2005-04-05
well, whattayaknow?! A typo solves the problem. Weird.

-Warr

---

### Post by mtron on 2005-04-10
Restarting dbus works, but when i remove the / in fstab, I get the error

*mount: special device dev/hda1 does not exist*

How did you manage to get this up running?

---

### Post by RastaMahata on 2005-04-10
[QUOTE=mtron]Restarting dbus works, but when i remove the / in fstab, I get the error

*mount: special device dev/hda1 does not exist*

How did you manage to get this up running?[/QUOTE]
 I think it the auto,user,exec,umask=000 thing.
For vfat, it would be```
auto,user,exec,umask=000
```
for ntfs, it would be```
auto,user,exec,umask=0222
```

I'll give this a try and report...

---

### Post by RastaMahata on 2005-04-10
well... it did work somehow, but all I could see was my hard drives mounted as 19g Hard Drive, and 30g Hard Drive. No names at all. And they didnt show up on Places.
But doing a```
sudo /etc/init.d/dbus-1 restart
```fixes this problem (somehow), but it takes out the pretty names from the drives (Floppy drive turns into Disquette1, etc)
I hope this get's fixed, and SOON.

---

### Post by stoneguy on 2005-04-10
FWIW, adding hal to the disk group and restarting dbus-1 changed the names like "19g Hard Drive" to the names of the mount points in /media. This was both on the desktop and in Places.

This is after the Warty to Hoary upgrade.

---

### Post by dodger on 2005-04-11
[QUOTE=stoneguy]FWIW, adding hal to the disk group and restarting dbus-1 changed the names like "19g Hard Drive" to the names of the mount points in /media. This was both on the desktop and in Places.

This is after the Warty to Hoary upgrade.[/QUOTE]
 what's the use of adding hal to the disk group?
i tried it, but it didn't change a thing. For me, the only thing that helps is restarting dbus-1. and i really get tired of doing it.

did anybody do a fresh install with the 'official release'? did the problem occur there, too?

---

### Post by stoneguy on 2005-04-11
Is there some script that's invoked when GNOME gets set up? That would be the ideal place to add the dbus-1 command. I know zip about how the flow of events around X and GNOME. Anyone?

---

### Post by Colsta on 2005-04-12
> 
/etc/init.d/dbus-1 restart

At the risk of posting a 'me too' ... err .... me too :)
Thanks for reassuring me that it wasn't a botched upgrade from Warty.

---

### Post by nixon on 2005-05-12
just upgraded to the latest breezy packages and my mounts are now showing up on the desktop!! first time since the release of hoary!.. stoked.. but am now living with the joys of a testing/unstable release.. follow me if you dare! muahaha.. ;-)

---

### Post by diebels on 2005-05-12
[QUOTE=stoneguy]Is there some script that's invoked when GNOME gets set up? That would be the ideal place to add the dbus-1 command. I know zip about how the flow of events around X and GNOME. Anyone?[/QUOTE]
 You could put it in the session properties. Run gnome-session-properties and add "gksudo /etc/init.d/dbus-1 restart" in the Startup Programs tab.

This requires the user to type in the password, but I guess you cannot avoid this since all programs in a gnome session is run as the user.

---

### Post by stoneguy on 2005-05-13
**SOLVED**

[QUOTE=diebels]Run gnome-session-properties and add "gksudo /etc/init.d/dbus-1 restart" in the Startup Programs tab.[/QUOTE]
Sounded good, but didn't work here. I tried fiddling with the run priorities too - thought maybe I needed to make it run earlier or later than the other 50s. All that did was affected the timing of the progress panel.

Putting the restart directly in gnome-session-properties didn't cut it. Instead, I created a shell script (named ~masteruser/bin/mydbusrestart) containing

[INDENT]#! /bin/bash
sleep 2
sudo /etc/init.d/dbus-1 restart[/INDENT]
Make mydbusrestart world-executable 

Using visudo, add the line

[INDENT]%users ALL=NOPASSWD: /etc/init.d/dbus-1[/INDENT]
Use System|Administration|Users and Groups|Groups to change the group membership of the Users group to include all the login users

In each user, use System|Preferences|Sessions|Startup Programs|Add
to create the command

[INDENT]/home/masteruser/bin/mydbusrestart[/INDENT]
so that when the Gnome session is set up, a dbus restart will occur at the end.

Thanks, diebels, for pointing me in the right direction.

I've added a backports request. I lack the sense of adventure of nixon and ali_baba  ;-)

Re backports request: we got a very quick response. Unfortunately it's [not what we'd hoped for](http://ubuntuforums.org/showthread.php?t=34378)

---

### Post by rickwood on 2005-05-19
Thanks for the info -- I'd also written a script but couldn't determine how to best make it run without a password on startup.  Looks like you've done what I was trying to do.  Just one question on what you said here:

[QUOTE=stoneguy]

Using visudo, add the line

[INDENT]%users ALL=NOPASSWD: /etc/init.d/dbus-1[/INDENT]
[/QUOTE]

To what config file do I add this line?

Thanks.

---

### Post by stoneguy on 2005-05-19
[QUOTE=rickwood]To what config file do I add this line?[/QUOTE]
If I told you you might accidentally kill yourself :smile: That's why you use visudo.

---

### Post by rickwood on 2005-05-26
Well, as risky as it was, I didn't kill myself! :)   The file is /etc/sudoers.  I didn't care for the visudo thing, as it seemed to bring up nano.  I much prefer either vi or gedit (of course I'm sure nano probably isn't that difficult to figure out either).

Thanks for the help, the script is now running nicely on login, and my drives show up fine in Places, Computer, and on the Desktop.

---

### Post by sparch on 2005-05-26
[QUOTE=rickwood]To what config file do I add this line?

Thanks.[/QUOTE]

/etc/sudoers

---

### Post by stoneguy on 2005-05-26
[QUOTE=rickwood]Well, as risky as it was, I didn't kill myself! :)   The file is /etc/sudoers.  I didn't care for the visudo thing, as it seemed to bring up nano.  I much prefer either vi or gedit (of course I'm sure nano probably isn't that difficult to figure out either)..[/QUOTE]

Well, if that's all that's bugging you, run it with
[INDENT]export VISUAL=/usr/bin/vi; sudo visudo[/INDENT]
I'm a vi guy myself ;-)

---

### Post by bored2k on 2005-05-26
[QUOTE=stoneguy]**SOLVED**[/QUOTE]

That worked :D

---

### Post by cbudden on 2005-09-02
[QUOTE=didit]i have a tricky way to show up windows drivers on your desktop in Hoary. What you can do is that
remove '/' in front of dev of your windows partition. For instance in my case:

dev/hda1 /mnt/winC 		vfat    auto,user,exec,umask=000 0 0
dev/hda2 /mnt/winD 		vfat    auto,user,exec,umask=000 0 0

with this trick then you will always have windows drives visible in Nautilus also on your desktop.
Hope this trick can help you

ps. new comer here... :)[/QUOTE]


This worked for me! Whoohoo

---

