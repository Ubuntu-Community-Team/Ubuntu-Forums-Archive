---
title: "crontab or gnome session startup for swap script?"
date: 2006-11-20
forum: Desktop Environments
---

### Post by archis on 2006-11-20
A question regarding the proper use of the GNOME session startup vs. crontab for a login command:

I have got a multi-boot setup with the swap area located on a USB drive and I am looking for a way to enable the swap at each login.

Normally, this would involve no more than adding the swap area to my fstab file, and this worked reasonably well under Breezy's boot-up sequence (which uses hotplug). Both Dapper and Edgy however are using udev which speeds up the boot sequence so much that the USB drive cannot initialize in time to be recognized and enabled via fstab. 

Therefore, the swap area residing on the same USB drive does not get initialized either. As a consequence, I need to run the command

[INDENT][FONT="Courier New"][COLOR="DarkOliveGreen"]sudo swapon -a[/COLOR][/FONT][/INDENT]

at each login in order to enable the swap area. My question is: how do I automate this login command properly - by adding it to crontab using syntax like

[INDENT][FONT="Courier New"][COLOR="DarkOliveGreen"]@reboot sudo /sbin/swapon -a[/COLOR][/FONT][/INDENT]

or do I create a small script, let's say

[INDENT][FONT="Courier New"][COLOR="DarkOliveGreen"]home/user/bin/swap[/COLOR][/FONT][/INDENT]

make it executable and add it to the GNOME session startup programs? Which approach is the right one with respect to this issue?

---

### Post by lloyd_b on 2006-11-20
You could add the "/sbin/swapon -a" command to "/etc/rc.local".  This is the last thing run by the init sequence, so hopefully your USB drive will have had a chance to initialize before it's run.

Lloyd B.

---

### Post by archis on 2006-11-20
Well the thing is, AFAIK, fstab does not 'get to try again' once we're past the moment when it is being queried during the boot process. -- This is precisely what [upstart]("http://upstart.ubuntu.com/"), the coming replacement for the currently used System V init process, is meant to address once it gets fully implemented from Feisty onwards: it will be able to query fstab 'on demand': that is, it will only query fstab about the USB drive once the drive is actually initialized, not as part of a fixed boot sequence - this will, it is hoped, lead to a faster boot-up as well because it will eliminate this and other bottlenecks between the hardware and the init process.

There's more information about upstart and how it works at its [Edgy spec page]("https://wiki.ubuntu.com/ReplacementInit"). Let me quote a few pertinent passages:

[INDENT][FONT="Courier New"][COLOR="DarkSlateGray"]The move to the 2.6 kernel and all the "hotplug" goodness that it provides has left us with several problems in dapper. Because the kernel can support hardware coming and going, and due to the increase in removable hardware, it's no longer possible to guarantee that particular devices are available at a particular point in the boot process.

The usual example is that dapper cannot mount USB disks in /etc/fstab because it is not guaranteed that the block device exists at the point in the mount process where that happens.

Another example is that of a network-mounted /usr; the network device needs to be detected, firmware loaded if necessary, any security layer on the connection negotiated and an IP address arranged before the NFS mount can occur. There are work-arounds to this, such as dapper which sleeps in the boot process until /usr is mounted, but they are hacky and an elegant solution is desired. 
[/COLOR][/FONT][/INDENT]

What happens right now however is that the USB drive volumes show up on my desktop anyway once I am logged into an account because they are being mounted 'as if I had just plugged the drive in' - i.e. they are being mounted with generic volume names such as 'usb volume 1', 'usb volume 2' etc., not the names I gave them in fstab. So I don't think they are being recognized at all before the actual account login, and I also think I will need to have to wait until actual login to run the [FONT="Courier New"][COLOR="DarkOliveGreen"]swapon[/COLOR][/FONT] command because the swap on the drive will be available only then. (correct?)

That's why I thought I would need to use either crontab or the GNOME mechanism or perhaps something similar. 

And so I wonder what best practice would be in this case? When is a crontab job with the [FONT="Courier New"][COLOR="DarkOliveGreen"]@reboot[/COLOR][/FONT] qualifier actually being executed - before login (i.e. when you see a gdm screen for example) or at/after login (i.e. as soon as the actual desktop is coming up)?

---

### Post by lloyd_b on 2006-11-21
> And so I wonder what best practice would be in this case? When is a crontab job with the @reboot qualifier actually being executed - before login (i.e. when you see a gdm screen for example) or at/after login (i.e. as soon as the actual desktop is coming up)?

The cron job will almost certainly run before you log in, since "cron" is completely independent of user logins.

Have you actually tried my "rc.local" solution?  You may find that this *is* late enough in the boot process for the drive to be available (or maybe not - I don't have a lot of experience with USB drives). But having a "swapon" command as part of the user login seems silly to me - this is a *system* level function, which should be performed even if no user ever logs in (as in the case of a server).

Lloyd B.

---

### Post by archis on 2006-11-21
lloyd_b, 

I have followed your advice and it works like a charm, thank you. It seems the USB drive initializes by the time rc.local is being queried. An elegant solution for my problem.

I was initally confused about the applicability of your advice because I was under the impression that Debian-based systems, unlike many other distros, actually don't use [FONT="Courier New"][COLOR="DarkRed"]/etc/rc.local[/COLOR][/FONT], as [a number]("http://www.justlinux.com/nhf/Distribution_Specific/Debian_GNULinux/Debian__Startup_Commands.html") of [sources]("http://plope.com/Members/chrism/debian_rc_local_equiv") point out. There's even a [wiki page]("https://help.ubuntu.com/community/RcLocalHowto") entitled '[Creating an rc.local equivalent for Debian/Ubuntu]("https://help.ubuntu.com/community/RcLocalHowto")' which is either outdated or inaccurate.

So yes, there **_is_** an [FONT="Courier New"][COLOR="DarkRed"]/etc/rc.local[/COLOR][/FONT] file, sourced by [FONT="Courier New"][COLOR="DarkRed"]/etc/init.d/rc.local[/COLOR][/FONT] (on Edgy at least) waiting for your customization. Unless you have fiddled with it before, there's nothing in it except a short explanatory note. Your startup commands should go just before the line saying [FONT="Courier New"][COLOR="DarkRed"]exit 0[/COLOR][/FONT]:

[INDENT][FONT="Courier New"][COLOR="DarkSlateGray"]#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR="DarkRed"]place your command here[/COLOR]

exit 0
[/COLOR][/FONT][/INDENT]

When you're done, test your work by invoking

[FONT="Courier New"][INDENT][COLOR="DarkRed"]$ sudo /etc/init.d/rc.local start
[/COLOR][/INDENT][/FONT]

[B]..stepping back:
[/B]
There are, it seems, quite a number of ways to achieve my goal of adding a simple startup command. I can add it to [FONT="Courier New"][COLOR="DarkRed"]/etc/rc.local[/COLOR][/FONT]; I could use a cron job to do it; or I *could* add it to GNOME's session startup programs. What I am interested in doing in this thread is to clarify what constitutes best practice. So please help me and correct the following if necessary:

1) [FONT="Courier New"][COLOR="DarkRed"]/etc/rc.local[/COLOR][/FONT] seems to be the best place to put most startup commands or scripts you might want to run, especially *system* level functions, which should be performed even if no user ever logs in, as lloyd_b points out.

However there are a few exceptions:

2) [FONT="Courier New"][COLOR="DarkRed"]cron[/COLOR][/FONT], in conjunction with the [FONT="Courier New"][COLOR="DarkRed"]@reboot[/COLOR][/FONT] string might be useful if you do not have access to root, for example if you are a non-root user (editing [FONT="Courier New"][COLOR="DarkRed"]/etc/rc.local[/COLOR][/FONT] requires root). See '[Debian Administration: Running scripts after reboot for non-root users]("http://www.debian-administration.org/articles/372")'.

3) Using the Session Startup Program tab of the GNOME session manager (in case you are using GNOME) or [KDE's Autostart]("http://www.kde.org/areas/sysadmin/startup.php#kdesktop") is useful when you want to run a command such as [FONT="Courier New"][COLOR="DarkRed"]xmodmap[/COLOR][/FONT] or [FONT="Courier New"][COLOR="DarkRed"]beryl-manager[/COLOR][/FONT] that [requires a running X server]("http://www.ubuntuforums.org/showthread.php?t=266174") or that is user-specific and should only run when a particular user logs in. In this case, neither rc.local nor cron will be useful because they are both part of the System V init process.

---

