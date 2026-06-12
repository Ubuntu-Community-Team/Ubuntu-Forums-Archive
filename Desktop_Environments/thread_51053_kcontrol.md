---
title: "kcontrol"
date: 2005-07-22
forum: Desktop Environments
---

### Post by sprucio on 2005-07-22
Everytime I try to change some settings in KDE via Kcontrol, I am asked to input the root password.

I use my current one and it does nothing. Is anyone else having the same problem?

---

### Post by Feanor on 2005-07-22
You can do

```
kdesu kcontrol
```

and do everything with privileges of administrator.

If you upgrade to kde 3.4.1 the bug seem to be fixed. In order to do this add to your repository list the following row

```
deb http://kubuntu.org/hoary-kde341 hoary-updates main
```

and then do

```
sudo aptitude update
sudo aptitude upgrade

```

---

### Post by sprucio on 2005-07-22
I take it that repository is one outside of ubuntu's site?

---

### Post by Feanor on 2005-07-22
I take it from [www.kubuntu.org](www.kubuntu.org) , but when you install some packet it say that there's no authentication... Don't worry, is just a warning is safer, and I use it a lot  ;-)

---

### Post by arjay1 on 2005-07-22
Sprucio - you will be glad to know it is not just you - see my post on this page - "can someone help with a quick test of control centre!!

For other readers:

BTW - I have upgraded to KDE 3.4.1 and this is STILL a problem.

For example- if I do kdesu kcontrol, it gives me access to Control Centre and I can edit the entries.  BUT THESE DON'T STICK.  If I apply the changes, exit Control Centre and then re-open control centre again, the changes have disappeared.  (In this case I need to enter the ip address for my router.  It goes in OK and then disappears!!)

Anyone any ideas?

---

### Post by sprucio on 2005-07-22
Have you tried adding that repository to your sources.list file?

I'm at work so I don't have access to a Linux machine but I'll post my results once I get to them.

---

### Post by arjay1 on 2005-07-22
It won't help you!  There is a major, major, bug in KDE 3.4.0 AND 3.4.1.   I have found it is well documented at bug number 8681 at bugzilla.ubuntu.com and 61850 at bugs.kde.org.

There are pages and pages of complaints - a quick google will get you there.

There are a few suggested workarounds but most only work for a few people.  The KDE developers suggest you switch to Gnome for the time being!!!!!!!!!!

I am going to try a couple of things (only a newbie I'm afraid) and I'll let you know if anything works.

Richard

---

### Post by sprucio on 2005-07-24
No luck on my end.

---

### Post by arjay1 on 2005-07-25
Hi - what have you tried since your last post?  I have managed to get a fix of sorts by doing this:

sudo kcontrol

Enter your password for sudo.  The control centre should open.

Choose the area you want to change and it should open for you.  Make your changes and choose "apply" BUT DON'T CLOSE AND EXIT.

Leave the control centre window open for 30 minutes or so and then close it.

Open it again and see if your changes are still there.

Good luck and let me know how you get on.

---

### Post by MikeyXX on 2005-07-26
[QUOTE=arjay1]Hi - what have you tried since your last post?  I have managed to get a fix of sorts by doing this:

sudo kcontrol

Enter your password for sudo.  The control centre should open.

Choose the area you want to change and it should open for you.  Make your changes and choose "apply" BUT DON'T CLOSE AND EXIT.

Leave the control centre window open for 30 minutes or so and then close it.

Open it again and see if your changes are still there.

Good luck and let me know how you get on.[/QUOTE]
 But doesn't this just make this fix work for the ROOT user...ie if it's a desktop change etc that is user specific it's going to write to the conf file with root privs. Then when you log out and in and it attempts to access/add/edit that file for the desktop you get an error.

---

### Post by arjay1 on 2005-07-26
Very good point - hadn't thought of that.  Actually, I haven't had any error messages but that doesn't necessarily negate your point.  

Unfortunately, for those of us who have this problem it is really serious and the only way we can get access to the control centre is through sudoing kcontrol.  Also this was the advice given in the kde bug site.  Unless you have looked at it you wouldn't believe the frustration and ill-will that is building up there over such a major bug.

The main problem I have had is when trying to modify network interface values. Even under sudo these would not stick beyond a reboot.  Maybe that is because of the point you are making.  However, even though i have managed to fix these by making changes direct to the interfaces file, there are many other changes I need to make where I don't know the CLI commands or the right files to modify (I'm new to linux and even newer to the appallingly flakey KDE.  I tried to switch to Gnome but after a couple of months of KDE I can't make head or tail of Gnome!!)  I have now managed to get samba up and working - not easy, again, if you cannot get into the samba definitions set up in control centre, but there are still other settings I need to change and it is driving me crazy.

Anyway - thanks for your comments - I'll have to give them some thought.

---

### Post by arjay1 on 2005-07-26
sprucio

Further tests of my workaround of leaving the control centre open after making changes have been only partially successful - it doesn't survive a reboot, for example. You really need to look elsewhere for a solution.

You never said what changes you were trying to make in control centre.  Was it anything to do with network settings?

If it was - I have followed advice in this forum about setting up the network connections by modifying the interfaces file.  What now works for me is these changes to the  file

[I]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
	mapping hotplug
	script grep
	map eth0

# The primary network interface

 iface eth0 inet static
 address 192.168.1.2
 netmask 255.255.255.0
  gateway 192.168.1.1
#  network 192.168.1.0[/I]

Note the commented out last line - if I leave this in, the network won't start.  Without it, the network boots OK and stays up after a reboot.


Sorry i can't help much more - only a newbie myself.

---

### Post by arjay1 on 2005-07-27
sprucio - still working on a solution for this.  Finally got help that seems to fix it:

[http://ubuntuforums.org/showthread....13&page=1&pp=10](http://ubuntuforums.org/showthread....13&page=1&pp=10)

1) Delete everything in /var/tmp/kdecache (the one with your username in it)
2) Check the /etc/kde3/kdm/kdmrc file. Somewhere in the file it says "RootLogin" - this should be set to true.

Needs a reboot.  Worth a try

---

### Post by sprucio on 2005-07-31
arhay1,

Can you post that link properly? It doesn't seem to be working. Thanks.

---

### Post by arjay1 on 2005-08-01
sprucio - sorry it didn't work:  I tried to cut and paste it again for you but it didn't work again.  It was a link in another forum post.  Go to the post below and page down until you find the link that won't work.  It works OK from there. In any case, the fix is nothing more than what is suggested in my post and/or in the link below:


[http://ubuntuforums.org/showthread.php?t=30893](http://ubuntuforums.org/showthread.php?t=30893)

Hope this is OK now.

---

### Post by Gezzer on 2005-08-01
have u setup a root password
open a konsole
write

sudo passwd root
enter

your pass word
enter

insert new root password twice

ensure root logon is enabled in the /etc/kde/kdm/kdmrc file

this will give u root access and should do as u require ...

---

### Post by arjay1 on 2005-08-01
Thanks for the tip - maybe others would like to use it if necessary.  Me, I have finally got my system set up using the CLI.  I am staying well away from kcontrol/Control Centre - it is as buggy as hell.

When I have an opportunity I am switching one of my machines to gnome and am going to try to learn that.  It sounds a lot more stable and there are much better help files around the internet.

Not happy about it because, as a newbie, I have spent weeks learning KDE and now I have to start all over again.  
BTW I can see it being the same for kubuntu.  I only tried it because mepis was completely unable to automount a digi camera, whereas kubuntu did it beautifully.

However, there are a load of other things kubuntu seems incapable of doing - enabling dual screen displays, mounting a floppy drive reliably and so on.  I've spent days trying to get these set up and had advice from lots of helpful and knowledgeable people but nothing doing.

It is amazing that 25 YEARS AGO I could put a floppy in a DOS machine, and later a Windows machine and have it automatically detected.  Seems linux can't do it 25 years later!!  Still have to manually mount and umount the drive and half the time it doesn't work ...

---

### Post by arjaybe on 2005-08-01
Arjay1:
"It is amazing that 25 YEARS AGO I could put a floppy in a DOS machine, and later a Windows machine and have it automatically detected. Seems linux can't do it 25 years later!! Still have to manually mount and umount the drive and half the time it doesn't work ..."

In what way was it "automatically detected?"  As I recall, the computer had no idea whether or not there was a diskette in the drive until you tried to access it.  Then it either read the disk if it was there or threw up an error if it wasn't.  Not much "automatic" there.

---

### Post by arjay1 on 2005-08-01
Yeah - sorry, not very well put was it.  I meant that if you put the disk in the drive the OS would ID and read the disk (hence all the old clicking and grinding) and then you could read it as you say.  Later, even in the earliest versions of windows you could click on the drive's icon and read what was on the disk.  That was "out of the box"  -  you didn't have to mount the drive first, and manually create an icon for it and so on.  That's what I meant.

---

### Post by Freddy on 2005-08-01
This is from a interview with Jonathan Riddell, (one of the master's of universe) one of the hardworking guys behind Kubuntu.

> DW: I noted on several forums that some users have been complaining about the quality of KDE packages in Kubuntu. They say that these packages are buggy and that Kubuntu is not as stable as Ubuntu. What can you say about this? Have you received any similar complaints?

JR: We did have some problems with overlapping files which took longer than it should have to get fixed due to the C++ transition blocking new packages in the archives. Other significant problems have included a beastie in KControl stopping you from using administrator rights, this is a general problem with KDE but seems to occur more frequently because of our sudo changes; Kopete was also caught out by a change in MSN's protocol which Gaim was fortunate enough to not be affected by. These are the sort of issues which happen to all distributions, but I am aiming for 100% bug free in Kubuntu Breezy :)

I'll can only hope that he succed in his misson to deliever a bug free Kubuntu next realese, and the kcontrol is more stable if you convert back to normal root access, witch I did a long time ago : )

You can read the hole interview on [http://distrowatch.com/weekly.php?issue=20050801#interview](http://distrowatch.com/weekly.php?issue=20050801#interview)

/happy hacking, freddy

---

### Post by Feanor on 2005-08-01
I hope too...

---

### Post by arjay1 on 2005-08-02
[QUOTE=Freddy]This is from a interview with Jonathan Riddell, (one of the master's of universe) one of the hardworking guys behind Kubuntu.

I'll can only hope that he succed in his misson to deliever a bug free Kubuntu next realese, and the kcontrol is more stable if you convert back to normal root access, witch I did a long time ago : )

/happy hacking, freddy[/QUOTE]

Thanks for the link to the interview.  At least he acknowledges the problem publically.  I think half the frustration comes from knowing that you must have a bug and no one being prepared to admit it.  Most newbies (myself included) often don't have the confidence to file a bug report - especially when they see the complicated and, necessarily formal, reporting procedure.

---

