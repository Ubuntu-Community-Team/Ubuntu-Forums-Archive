---
title: "DBUS/gnome volume manager problem?"
date: 2005-04-14
forum: Desktop Environments
---

### Post by bawbag on 2005-04-14
I've seen this listed  a couple times in the forum and I was wondering if there was a fix or temporary solution yet?

Basically the mounts to /media in fstab do not show up in computer:///.  If DBUS is manually restarted ( /etc/init.d/dbus-1 restart ) everything shows as normal.  This affects Windows and ext3 partitions.  CD/DVD appear to work as they should.

I haven't found a fix in the forums, but if anyone could suggest a quick-fix, like a way to automatically restart dbus when Gnome runs, it would be much appreciated.

TIA.

---

### Post by bawbag on 2005-04-21
*bump*

---

### Post by Calvin on 2005-04-21
[QUOTE=bawbag]*bump*[/QUOTE]
 I'd also be interested in a fix of this very annoying bug...

I have exactly the same problem as bawbag described, but it also leads to some other issues, namely:

- When I plug in my camera, or when I put my memory card in my card reader (which is already plugged in at boot), there's nothing appearing on the desktop IF my computer has just been started. That makes it really difficult to understand: when the computer has been started for some time (couldn't measure exactly how much), there's no problem with plugging in my camera, it shows up as it's supposed to (and I have this dialog box asking me if I want to import the pictures).

- When I start my computer, if I restart DBUS manually as described by bawbag, it works. BUT if I wait for some time before restarting DBUS, then I have an error message saying that "hald is already started", and everything seems to be buggy afterwards (I have error messages from update-manager and another app complaining that they're not able to contact the HAL daemon)

- I also have an issue with Totem that I think is related to this whole HAL problem: when the computer is started, I have no problem starting a video, but if I wait for some time, totem takes a lot of time starting up, and shows an error message if I start it with the Terminal:
**libhal.c 2282 : Error sending msg: No reply within specified time**


So, my conclusion is that there might be a problem with the HAL dameon in Ubuntu Hoary. I've been searching in Bugzilla and all the filed bugs that could be related seem to be unresolved or without any reply since the official release of Hoary.

I'd gladly help the developers to fix this by giving them details about my described problem. Maybe I should file a new bug with these details...

Any suggestion, or confirmation of these bugs would be welcome!

---

### Post by bawbag on 2005-04-21
I hope this doesn't get overlooked by the Hoary team.  I found the whole Dbus/GVM thing to be tempramental throughout the Hoary testing phase, but it was working very well until we came close to final release.

Also, and I'm not entirely sure if this is related to HAL or Gamin, but I've found that the desktop fails to refresh properly sometimes.

For example if I extract a tarball to desktop, I need to manually press Ctrl+R to refresh before it will show up.  Sometimes though it works fine.  If I create a folder on the desktop using the console, it appears immediately.

These are hardly major usablity problems, but it would be nice to know the devs are at least working on bug fixes for Hoary, and not just security patches.

---

### Post by duff on 2005-04-28
Any news on this problem?  This happens on all 3 computers I have Ubuntu Hoary installed on.  I don't get it..I have everything completely up to date, but I don't see the devices on my desktop until I restart dbus, and my usb stick has no icon.  The Live CD works as expected though.  ](*,)

---

### Post by stoneguy on 2005-04-29
This has been floating around unanswered in various threads for around a month now.

As I said in an earlier thread [http://www.ubuntuforums.org/showthread.php?t=21508](http://www.ubuntuforums.org/showthread.php?t=21508) , I'd settle for some way to get the *dbus-1 restart* rerun later in the course of gnome startup. But that startup process is not readily understandable.

This problem prevents me from converting friends to Linux. I don't mind spending some time installing and configuring their systems, but they've got to have access to their Win shares from desktop without resorting to the command line. 

The lack of an answer for this problem is my major annoyance with Ubuntu at this time.

---

### Post by duff on 2005-04-30
[QUOTE=stoneguy]I'd settle for some way to get the *dbus-1 restart* rerun later in the course of gnome startup. But that startup process is not readily understandable.[/QUOTE]
For my problems, that won't fix it.  Restarting dbus only shows those devices that are already plugged in.  If I remove that device, add a different it won't show up until I restart dbus again.

**EDIT:** BTW, is this affecting anybody with a fresh Hoary install, or only those of us that upgraded from Warty?

---

### Post by stoneguy on 2005-04-30
[QUOTE=duff]For my problems, that won't fix it.[/QUOTE]

Of course. You need it fixed **properly**. Given the lack of attention so far, I'll settle for a patch job.

I'm also a warty upgrader BTW. Maybe we should poll for experiences?

---

### Post by mtron on 2005-04-30
Nope, had the same problem when upgrading, did a fresh install (had some problems with backports), but still the same. 

What's very strange is that it works sometimes, and sometimes not... 

I would expect it working or not working, but this behaviour is strange. Tried to find differences in the logfiles from non-working to working boot, but i did not suceed...

---

### Post by stoneguy on 2005-04-30
[QUOTE=mtron]I would expect it working or not working, but this behaviour is strange. Tried to find differences in the logfiles from non-working to working boot, but i did not suceed...[/QUOTE]

Probably not as strange as you think. And no, I'm not surprised there's nothing in any logfiles.

I suspect there are 2 problems. One (which I fix by merely rerunning dbus) has to do with when dbus is run when the desktop is set up. Your particular complaint probably relates to some sort of event notification deficiency.

During startup, there's a reference to *dbus-launch*  in /etc/X11/Xsession.d/75dbus-1-utils_dbus-launch. It gets concatenated into the STARTUP variable that is finally executed in 99xorg-common_startup (it appears that Xsession.d is analogous to init.d in principle). Unfortunately, I can't fix my problem by inserting *dbus-1 restart* at the end, since STARTUP is *exec*'d. I don't know where or whether I could add something useful to Gnome startup (global or personal) that would do the trick.

EDIT: My symptom has been logged as Bugzilla #8269. No activity since Hoary release though. Your issue may be referenced in Bugzilla #6879.

---

### Post by gbusse on 2005-05-01
This bug has really been um well bugging me to no end as well. I love Ubuntu and have been using it since Warty but it almost seems as though even though bugs have been filed and dozens of posts have been created about this problem that there is no action being taken. There is not even any response from the developers? I appreciate all of the work they do. But wouldn't even a small note in the forums stating that:

We are aware of the bug but it won't be addressed until Breezy is released

or

We expect to have a fix for this bug soon

or

We have more important things to worry about right now

But there is nothing, that I have found anyways. In other distro's such as Fedora or Gentoo, the developers participate in the forums all the time helping people solve issues.

I know this is free software and I know I cannot expect too much from it, but how about having a developer just say something?!?

Because quite frankly this bug is also keeping me from recommending Ubuntu to my Windows based friends as well.

I'll step off my soap box now...

Thanks,
Gord

---

### Post by duff on 2005-05-01
[QUOTE=mtron]Nope, had the same problem when upgrading, did a fresh install (had some problems with backports), but still the same. [/QUOTE]

Did this fresh install involve reformatting your partitions, or did you just reinstall on top of your old install?  It's just weird that the LiveCD works as expected, but all 3 of my upgrades don't.  I've even tried creating a new user to see if it worked under a fresh account, but it didn't.  I thought (hoped) maybe there was a system-wide config file screwing it up.

---

### Post by bjunix on 2005-05-04
i face the same problems and hoary is my first ubuntu installation. before that i used debian sarge, but i reformated all my partitions.

i hope there will be a bugfix soon.
i really like ubuntu, but this bug is very annoying.

---

### Post by stoneguy on 2005-05-04
I'm starting to feel a bit pessimistic about this situation :sad:

There are 3 or 4 components relevent to this problem: gnome-volume-manager, dbus, hal, and perhaps another whose name slips my mind. Problems with these are being mentioned on the Gnome, Debian, and Gentoo sites. It's not just an Ubuntu problem - it's upstream - how far, I can't determine.

One possibly bright side is that Ubuntu's Martin Pitt has been involved in providing g-v-m fixes to Debian. I suspect he's the guy that would most appropriately give us some advice on how to deal with our problems. It would be nice to hear from him in this thread.

---

### Post by rickwood on 2005-05-04
I've got this problem too.  I also reported it as a bug.

---

### Post by titus1950 on 2005-05-09
This Is my temporary solution,hoping that the people that really knows can do something about it.
Hi,I did this the newbie way,because I am,
1-I follow the Guide to mount my vfat partition.
2-I follow the guide to log in as root.
3-As root go to media and find your windows mounted partition,then right clic on it 
....Make Link, make one, Give all Permissions to it and leave it there.
4-Log in as user,as you normaly do,and go to Media,find the Link you just made and copy it to your Desktop,and now you can rename it or change the folder for an Icon...Etc,Etc .And when you boot ! IT WILL BE THERE FOR YOU.
That was my newbie Solution...hope will help somebody.
Good Luck.

---

### Post by rickwood on 2005-05-09
Thanks titus1950 for the suggestion.  I used links for a while, but it became really annoying when hal/dbus would work as advertised.  Then I had two sets of drive icons on my desktop.  Not very optimal, either.  So for now, I've got a shell script that I run manually after each logon when hal/dbus doesn't work right.  It's still very annoying, but it gets the job done.

---

### Post by infinito on 2005-05-11
This problem is covered under [bug #7641](https://bugzilla.ubuntu.com/show_bug.cgi?id=7641).
It seems very strange to me that people at Ubuntu is not fixing this, 'cause I think this is one of the ugliest bugs I ever seen on a stable distro.

You can't see your mounted partitions. Sometimes removable media doesn't mount. iPod works randomly. Is this really linux for human beings? Or linux for people who know about '/etc/init.d/dbus-1 restart'?

It's been a month since Hoary release, and this bug is still not fixed. I think Ubuntu is GREAT, but this kind of things (maybe it won't be fixed till Breezy??) makes me think going back to Debian...

Hope this will be fixed soon... hope...

---

### Post by Alexander Kirillov on 2005-05-11
[QUOTE=infinito]This problem is covered under [bug #7641](https://bugzilla.ubuntu.com/show_bug.cgi?id=7641).
It seems very strange to me that people at Ubuntu is not fixing this, 'cause I think this is one of the ugliest bugs I ever seen on a stable distro.

You can't see your mounted partitions. Sometimes removable media doesn't mount. iPod works randomly. Is this really linux for human beings? Or linux for people who know about '/etc/init.d/dbus-1 restart'?

It's been a month since Hoary release, and this bug is still not fixed. I think Ubuntu is GREAT, but this kind of things (maybe it won't be fixed till Breezy??) makes me think going back to Debian...

Hope this will be fixed soon... hope...[/QUOTE]
 Well, I am certain the developers are working on this - but not every bug can be easily fixed. So I am willing to wait patiently. What I would appreciate, though, is one of developers just telling us what is the status of it - and when we could expect some  fixes...

Meanwhile, I've added myself in CC for this  bug, and will watch it closely.

---

### Post by bjunix on 2005-05-11
i ll also wait patiently. But i do not understand what the problem is about. 

i can live with the "not showing mounted media icons". but there are also problems with dbus/hal concerning my video playback. thats the most annoying issue.

---

### Post by stoneguy on 2005-05-11
As I said previously, I'm not certain "the people at Ubuntu" *can* fix this. It's affecting other distros as well.

What rankles me is not having any acknowledgment from  "the people at Ubuntu". I also can't help but wonder whether Hoary would see a fix even if it's delivered. After all, this isn't a security issue. OTOH, Breezy is a long way off.

The LUG here is scheduling an InstallFest next month. I'd like to go there with a copy of Hoary for people to try out. But if newbies can't connect to their Windows side easily, I don't think there'll be too many takers.

---

### Post by infinito on 2005-05-11
[QUOTE=stoneguy]The LUG here is scheduling an InstallFest next month. I'd like to go there with a copy of Hoary for people to try out. But if newbies can't connect to their Windows side easily, I don't think there'll be too many takers.[/QUOTE]

I agree with you.... by now, I won't recommend Ubuntu to any newbie.

---

### Post by Ali_Baba on 2005-05-14
Manage to get my cdrom automount and hopefully this bug fixed with this [http://www.ubuntuforums.org/showthread.php?t=31734](http://www.ubuntuforums.org/showthread.php?t=31734) :)
dist-upgrade to breezy and changing all hoary sources to breezy worked.

---

### Post by drigloi on 2005-05-15
Dear Ubuntu fellows,

I think I have an idea regarding this issue described here as I'm also a user of a Hungarian distribution ([www.uhulinux.hu](www.uhulinux.hu)) also based on the Gnome 2.8/hal/dbus system. I'm not a developer of that distrib only a curious user but I had some role resolving the similar hal/dbus instability problem. During development of the current stable release of that distro I noticed that the hal/dbus system didn't worked for me while it worked for the developers and other testers. The developers first didn't have an idea why the system worked for some users and why not for others.

During an ssh assisted debugging process led by a developer of that distro we found out that the problem originates from a hal/dbus bug. In that distro the initscripts first start the hal (Hardware Abstraction Layer) daemon and in the next step starts the dbus service. Because my PC is quite a fast one (P4 3066 HT, 1 GB Ram) and due to some errors of hald, the hal daemon couldn't initialize fast enough before dbus was started. We introduced a small delay after the hald startup process (a simple sleep 5 command) thus letting hald properly initializing so launching dbus after solved the issue. After this developers introduced some kind of patching to the hal/dbus so it is now working without problems on any PC configuration.

I've checked the Ubuntu initscripts but unfortunately I still don't know enough about the Ubuntu startup process so I haven't found how hald is launched in Ubuntu. So the task of resolving this issue remains for the more experienced Ubuntu users/developers but I think I have just given a good idea for starting the work.

I think the fact that dbus works out of the box in the Ubuntu Live is because booting from CD takes significantly more time and the slower boot up process gives the chance of proper hal initialization.

I hope this will help you because I like Ubuntu very much.

---

### Post by duff on 2005-05-15
Do you have that order correct?  You mean insert a delay after the dbus daemon starts, so it is initialized before hald is activated, right?

---

### Post by drigloi on 2005-05-15
Yes, you're right. Dbus first and hald then. But I remember that we put delay after hald startup, not dbus.

Also after customizing UHU-Linux I managed to speed up the boot process (disabled unneeded services, removed initrd which my system doesn't need) so much that hald started to act strangely again. I realized that when hald finishes its initialization rutines my floppy disk drive gives out a special sound (like checking for floppy) and if that sound came BEFORE gdm start everything was OK but if AFTER gdm startup the hald/dbus system and even Nautilus failed to operate. I could play with the Scroll Lock key during test boot-ups and found that if I press Scroll Lock AFTER hald start till I hear the floppy drive seeking there were no problems. I decided not to implement another sleep () delay but instead I have rearranged the boot services' startup order (e.g placed the network+DHCP and some other services AFTER the dbus/hald init) thus maintaining the fast boot up sequence - and as hald has more time before gdm to start I have no problems with hal anymore.

---

### Post by Alexander Kirillov on 2005-05-16
[QUOTE=drigloi]Yes, you're right. Dbus first and hald then. But I remember that we put delay after hald startup, not dbus.

Also after customizing UHU-Linux I managed to speed up the boot process (disabled unneeded services, removed initrd which my system doesn't need) so much that hald started to act strangely again. I realized that when hald finishes its initialization rutines my floppy disk drive gives out a special sound (like checking for floppy) and if that sound came BEFORE gdm start everything was OK but if AFTER gdm startup the hald/dbus system and even Nautilus failed to operate. I could play with the Scroll Lock key during test boot-ups and found that if I press Scroll Lock AFTER hald start till I hear the floppy drive seeking there were no problems. I decided not to implement another sleep () delay but instead I have rearranged the boot services' startup order (e.g placed the network+DHCP and some other services AFTER the dbus/hald init) thus maintaining the fast boot up sequence - and as hald has more time before gdm to start I have no problems with hal anymore.[/QUOTE]
 Please add this to [bug 7641](https://bugzilla.ubuntu.com/show_bug.cgi?id=7641) -it may be of some help to devleopers (who may not be reading this thread).

---

### Post by mike'o on 2005-05-16
I was happily surprised when I inserted my first CD to the drive. An icon was soon created on the desktop and the CD started.  :grin: Same thing with my Canon digikam. I was not getting this effect with SuSE 9.1 (KDE 3.2 - I had some serious problems with automount not wanting to release my CD's after using K3B, the CD roaster of KDE) and surely not on Windows ME, so I thought 'this is cool!'
So obviously automount works on my machine, which is not so new and fast anymore. Maybe it's this initialization sequence, that drigloi mentioned, and my Duron 1300 Mhz is slow enough to make things start in the right order. I have also an antique hard drive on which I installed Ubuntu that is slowing the system down (didn't wan't to mess my SuSE and WinME before I had tested this one for good).
I have used the update agent so my system is up to date. And it still works! Wow  ;-)

Sorry for you who can't enjoy this ability now, but I just wanted you to know that this is not an universal problem.

Mike

---

### Post by clarke.rainey on 2005-05-16
Well mine worked for a while on my desktop, which was an upgrade from Warty to Hoary... I do not have anything special installed other that the defaults plus most of the stuff in the How To... however about a week ago my 250GB EXT HD and 20GB mp3 player would no longer mount automatically... not a big deal for me because I can just "sudo mount /dev/sda1 /media/250drive -t vfat umask=000" after I reboot my computer every few weeks, and do that same thing for my mp3 player when I change files on it every so often, but I would like to try and help the Ubuntu developers figure out what the problem is... is there any way I can send them all of my system info that would be helpful to them?..

---

### Post by duff on 2005-05-16
[QUOTE=drigloi]Yes, you're right. Dbus first and hald then. But I remember that we put delay after hald startup, not dbus.

Also after customizing UHU-Linux I managed to speed up the boot process (disabled unneeded services, removed initrd which my system doesn't need) so much that hald started to act strangely again. I realized that when hald finishes its initialization rutines my floppy disk drive gives out a special sound (like checking for floppy) and if that sound came BEFORE gdm start everything was OK but if AFTER gdm startup the hald/dbus system and even Nautilus failed to operate. I could play with the Scroll Lock key during test boot-ups and found that if I press Scroll Lock AFTER hald start till I hear the floppy drive seeking there were no problems. I decided not to implement another sleep () delay but instead I have rearranged the boot services' startup order (e.g placed the network+DHCP and some other services AFTER the dbus/hald init) thus maintaining the fast boot up sequence - and as hald has more time before gdm to start I have no problems with hal anymore.[/QUOTE]

Well, I removed gdm from startup, to make sure I could start it dead last, and I've put `sleep 10` in both dbus and hald (it's in */etc/dbus-1/event.d/20hal*, BTW), before and after their start-stop-daemon calls, but I'm still having problems.  CDs are automatically mounted, but my hd partitions that are automatiicaly mounted through fstab aren't being shown on the desktop, and USB automounting is flakey.

---

### Post by stoneguy on 2005-05-16
Have a look [here](http://ubuntuforums.org/showthread.php?t=21508) for a partial solution.

---

### Post by derrick1985 on 2005-05-16
[QUOTE=duff]Well, I removed gdm from startup, to make sure I could start it dead last, and I've put `sleep 10` in both dbus and hald (it's in */etc/dbus-1/event.d/20hal*, BTW), before and after their start-stop-daemon calls, but I'm still having problems.  CDs are automatically mounted, but my hd partitions that are automatiicaly mounted through fstab aren't being shown on the desktop, and USB automounting is flakey.[/QUOTE]

I currently have a few of the same bugs as you do. I added my partitions manuallt (a ntfs and fat32) and both don't show on the desktop. BUT, when i insert a cd, it shows. USB takes a little time to show, but it does show.

I also haven't added the sleep command, as right now i'm using breezy (even though when i go about, it shows up as 5.04) because mine just failed altogether a few days ago, and i got tired of it.

Anyways, where would i find where i put the sleep command. Because, i want to compare the current ubuntu startup file (5.04) to the new breezy one, and see what if any changes have been made.

---

### Post by drigloi on 2005-05-19
For USB problems I heard a workaround, try sudo rmmod ehci-hcd then restart dbus.

---

### Post by Stormy Eyes on 2005-05-19
[QUOTE=Ali_Baba]Manage to get my cdrom automount and hopefully this bug fixed with this [http://www.ubuntuforums.org/showthread.php?t=31734](http://www.ubuntuforums.org/showthread.php?t=31734) :)
dist-upgrade to breezy and changing all hoary sources to breezy worked.[/QUOTE]

Upgrading to Breezy is a bad idea at the moment, as they're upgrading the compiler from GCC 3.3 to GCC 4.0, which requires rebuilding all apps written in C++. Expect breakage for the next month or so.

---

### Post by Ali_Baba on 2005-05-19
Yeah,I think I wont update for a moment now :) its working ok at the moment.

---

### Post by derrick1985 on 2005-05-19
[QUOTE=Stormy Eyes]Upgrading to Breezy is a bad idea at the moment, as they're upgrading the compiler from GCC 3.3 to GCC 4.0, which requires rebuilding all apps written in C++. Expect breakage for the next month or so.[/QUOTE]
So that's what happened.

---

### Post by Bavo on 2005-05-24
I'm having troubles with automount too. I can live with that, but sometimes it gets me into some more serious problems.

I have a USB-disk, USB-stick and a DVD/CDROM wich all cause me troubles.
Whenever i insert any of those it gets mounted (most of the times) nautils opens it and I can access the files.
It is all accessible trough /media/ but nothing shows up in computer:/// 
sometimes it shows up after i do a dbus-1 restart

The problem is that I don't get them unmounted , so this means that I insert one disk per session (and i can plug my usb-hdd and usb-stick in once a session)
If i dare to put in a new disk, i can't shut down my computer anymore.
It just hangs on --- Halting system now --- or -- Rebooting system now ---

If I do a kill -9 -1 there is a mount process and hald that keeps living

Does anyone know how to solve this issue.

---

### Post by Burgundavia on 2005-05-24
For informations sake, most of the developers almost never read the forums. 

Now, before you all jump on them, there are 2 cultures clashing here. The forum culture is very different from the mailing-list culture. Most of the Ubuntu devs are old Debian devs, and thus mailing list people.

If you have ideas and fixes, come to the ubuntu-devel list (not bug reports, but bug fixes)

Corey

---

### Post by WakkiTabakki on 2005-06-02
I believe I found a fix for this all... Could someone verify this...

Background:
I have exactly the same problem as stated in this thread. My mounts only show up on the desktop after I do a ```
/etc/init.d/dbus-1 restart
```. If I pop a CD in or attach my usb drive, the icons usually do pop up, even without a restart of the dbus.
I had warty installed and  dist-upgraded to hoary, with the same prob. When Hoary was released, I did a fresh install; same prob.

Steps: 
1. Download BUM, boot-up-manager
[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html) 
1.1 Install it (duhh...)

2. Change the strart-up priority of DBus (yes, it could just as well be done manually, but then you would miss out on an excellent opportunity to use an app called "bum"...)
2.1 Start BUM (under menu System/Administration)
2.2 Go to the "Standard runlevel" tab
2.3 Scroll down till you find dbus-1, right-click and choose 'Change start/stop priority'
2.4 Set it to 21
2.5 Reboot

It's been two days and I've been rebooting numerous times, and the icons are always there at boot (with the proper mount names, not the '20G disk'). Normally I'd only get the icons once in every couple of boots...

Does this work for anyone else?

Cheers
N

---

### Post by mtron on 2005-06-02
great. fixed it for me too! 

Thanks a lot for that.

---

### Post by infinito on 2005-06-02
Didn't work here :(

---

### Post by AndyAWS on 2005-06-02
Did not work for me either... :???:

---

### Post by mtron on 2005-06-04
nope.. was too early, after i rebooted my machine for the first time since 2 weeks it's again messed up.

Does it also affect debian testing / unstable or the upcoming sarge?

my last debian sid (~ Oktober 2004) did not show this behaviour. 

Also the suggested dbus restart script is also not a good solution. It shows the desktop icons of the mounted partitions, but when i plug in my ipod it requires again a restart to show it.

I searched the devel mailing list, but it seems that there was not any progress till now.

---

### Post by WakkiTabakki on 2005-06-04
[QUOTE=mtron]nope.. was too early, after i rebooted my machine for the first time since 2 weeks it's again messed up.
[/QUOTE]

Yep, same here, sorry to say... It worked perfectly for about 4 days, through countless reboots. 

But now it's bust again...

/N

---

### Post by bjunix on 2005-06-04
thus, hotplug not working, right?

it keeps me frustated. wheres the point of dbus/hald problems concerning hotplug.

i can mount hotplug partions manually? and static partions via fstab. whats about "auto-mounting" my fat32/ntfs/hotplug partions? i really do not need. but noob as i am i dont know how to deactivate those "things".

i know how to mount partions or how to edit fstab properly but i don not know how to deactivate hotplug!

---

### Post by titus1950 on 2005-06-17
I did something found reading the forum and it** fixed the problem**
Find this In   etc/fstab
   /dev/hda1      /media/windows 	vfat    umask=000       0 

And change for this
   dev/hda1      /media/windows 	vfat    umask=000       0

just erase the line in front of deb/hda1..................................................
That worked for me.
Don't forget to REBOOT.

---

### Post by mtron on 2005-06-17
[QUOTE=titus1950]change for this
   dev/hda1      /media/windows 	vfat    umask=000       0

just erase the line in front of deb/hda1..................................................
That worked for me.[/QUOTE]

What do you want to say?

i can't follow...

This problem has nothing to do with your fstab, or how you mont a vfat partition. As others posted it's more likely a  hotplug / dbus / kernel issue.

---

### Post by titus1950 on 2005-06-17
Sorry ,but this is only to show windows on your desktop and places like in warty,without doing a     (sudo /etc/init.**d/dbus**-1 restart)·...Password....enter...
every time you bootup.

---

### Post by infinito on 2005-06-18
[QUOTE=titus1950]Sorry ,but this is only to show windows on your desktop and places like in warty,without doing a     (sudo /etc/init.**d/dbus**-1 restart)·...Password....enter...
every time you bootup.[/QUOTE]
 This problem is about showing partitions on desktop, Places menu, and with correct names on Computer folder. Your trick only get the correct names on Computer folder, but icons are still not displayed on desktop... At least at mine...

---

### Post by titus1950 on 2005-06-18
[QUOTE=infinito]This problem is about showing partitions on desktop, Places menu, and with correct names on Computer folder. Your trick only get the correct names on Computer folder, but icons are still not displayed on desktop... At least at mine...[/QUOTE]





 

On my PC's  It shows in all 3 places,desktop,places and computer.

My PC/ P4.3Ghz,MOBO Intel Perl ,256 Ram and Sata 80Gb

But it could be that this only works on same computers,on my Toshiba laptop
A10 it works Perfectly

---

### Post by stoneguy on 2005-06-19
For anyone wanting to see whether Breezy solves this problem for them, Andreas Mueller (whose Gnoppix project is now under the Ubuntu umbrella) creates a 05.10 Live Beta at [http://source.rfc822.org/pub/local/gnoppix/gnoppix/beta/breezy/](http://source.rfc822.org/pub/local/gnoppix/gnoppix/beta/breezy/)

Collectively, the workarounds are really just voodoo. It's funny reading the conjectures about how the delay values correlate with CPU speed. My own machine is 500Mz, so I don't consider that factor relevant :)

---

### Post by infinito on 2005-06-19
[QUOTE=titus1950]On my PC's  It shows in all 3 places,desktop,places and computer.

My PC/ P4.3Ghz,MOBO Intel Perl ,256 Ram and Sata 80Gb

But it could be that this only works on same computers,on my Toshiba laptop
A10 it works Perfectly[/QUOTE]
 OK, I'm sorry, it worked! Just need to reboot (i'm not reboot the computer very often).
So for everyone with this error, titus1950 workaround on fstab just works!

Thanks!

---

