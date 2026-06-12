---
title: "KDE auto mounting USB devices and media:/ file system"
date: 2006-06-09
forum: Desktop Environments
---

### Post by DaveQB on 2006-06-09
I have updated my system from Breezy to Dapper.  Other then hal and udev missing and needing re-installed, its all ok.  Now I have a system here thats a clean install of Dapper and this problem has arised.  Never had this before.

When I plug in a USB device I get the usual pop up and I then clock in "Open in New Window"

Konqueror pups up with url media:/sda and then up pops this error.

[IMG]http://dward.us/pics/mount-error.png[/IMG]

This is the same error one would get if trying to mount from a terminal with it being in fstab etc.

My first though is I need to set the sticky bit on the mount command.  But I shouldnt have to do this, shouldnt this work right out of the box ?

I could also edit the fstab file too, but again, I shoudnt need to.

So... what does KDE use to do this mounting and why is it being denied ?

---

### Post by arizonagroovejet on 2006-06-09
I have got that same error when the user I was logged in as wasn't the member of a necessary group. I think the relevant group in this case is plugdev. (You probably want them to a member of some other groups too like audio and cdrom.)

If they're not in the plugdev group try adding them. 

You can add them manually or there's a thread here [http://ubuntuforums.org/showthread.php?t=31542](http://ubuntuforums.org/showthread.php?t=31542) which describes how to automatically make all users members of certain groups when they log in.

---

### Post by DaveQB on 2006-06-09
Thanks for the reply.  I too found this to be the cause from some top blokes on #kubuntu.

With that fixed, but question/problem is, why wasn't this addition user (first user created was in this group, but this the 2nd user created, was not) added to the plugdev group ?  How will a new user be able to work this kinda problem out ?
Granted if it was an upgraded machine, things can go wrong, but this is a clean install of Dapper.

I am a Linux promoter in that I push it where ever and whenever I can, but these little things can be show stoppers.  Dont we agree ?

---

### Post by arizonagroovejet on 2006-06-10
[QUOTE=DaveQB]I am a Linux promoter in that I push it where ever and whenever I can, but these little things can be show stoppers.  Dont we agree ?[/QUOTE]

I agree. I can see the logic in subsequent users not being automatically added to say, the admin group. Mac OS X also uses the same aproach to administration by not having the root user disabled and with that any new users created subsequent to the one you create during the installation process do not have admin rights unless you specifially tick the box for it.

However I think it is a huge flaw in (K)Ubuntu that newly created users are not automatically added to groups such as plugdev, audio, cdrom, etc. If they aren't in those groups then from their point of view the OS is essentially broken.

---

### Post by DaveQB on 2006-06-12
[QUOTE=arizonagroovejet]I agree. I can see the logic in subsequent users not being automatically added to say, the admin group. Mac OS X also uses the same aproach to administration by not having the root user disabled and with that any new users created subsequent to the one you create during the installation process do not have admin rights unless you specifially tick the box for it.

However I think it is a huge flaw in (K)Ubuntu that newly created users are not automatically added to groups such as plugdev, audio, cdrom, etc. If they aren't in those groups then from their point of view the OS is essentially broken.[/QUOTE]

Very much agree.  Admin group is another story, but basicly functional things like this ....

I haven't tested yet, but this is the default behaviour of a clean install of Dapper ?  
That is an odd decision by the developers.  If a user can't plug in their MP3 player to put music on it then its gonna cause grief no end.

And seriously, you can't argue the 'security' issue on that one, people need to use ***their*** computers.

---

### Post by arizonagroovejet on 2006-06-12
I have submitted this issue as a bug. If you anyone wishes to add their own opinions/experiences the bug can be found at

[https://launchpad.net/distros/ubuntu/+bug/49504](https://launchpad.net/distros/ubuntu/+bug/49504)

---

### Post by arizonagroovejet on 2006-06-13
[QUOTE=DaveQB]Very much agree. .[/QUOTE]

Well I'm glad someone does. Sadly the Ubuntu developers do not. The bug has been rejected because

"If you use the GUI tools, there are options for adding administrative
privileges (ie. those group memberships). If you are adding users
through the command line, you should know that Linux users do not by
default have administrative rights."

The command line point is fair enough, although it wasn't the admin group I was concerned about. The issue remains though, how are people supposed to know they need to add these group memberships?

Maybe there's someone better to submit this other than as a bug?

---

