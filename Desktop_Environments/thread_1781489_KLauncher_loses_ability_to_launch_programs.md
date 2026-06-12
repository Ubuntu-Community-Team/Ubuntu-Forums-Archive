---
title: "KLauncher loses ability to launch programs"
date: 2011-06-13
forum: Desktop Environments
---

### Post by cybermac912 on 2011-06-13
This is finally frustrating me enough to ask about it. I've been experiencing this since (I think) the Natty upgrade, on 2 different machines -- my home desktop and my VM guest at work.

The problem is that KLauncher seems to periodically lose the ability to launch programs. Sometimes an error dialog pops up: "Error launching /usr/share/applications/kde4/ksysguard.desktop. Either KLauncher is not running anymore, or it failed to start the application." (I verified that KLauncher is in fact still running). Other times, the pointer icon bounces and the placeholder shows up in my task bar, but then it all goes away without any error.

There doesn't seem to be any pattern as to what's running when this happens, or how much memory is in use, or what I launch, or anything else. Sometimes, if I start closing apps that are already open, then the thing I tried to launch will  start up. Other times, I have to actually log out and back in before I can get anything to start. Other than that, the desktop continues to behave normally. Nothing seems to be locked up or anything. It's very strange.

Does anyone have any ideas what might be going on? This is getting in my way enough that I'm seriously considering GNOME3 :shock:

---

### Post by logichype on 2011-06-16
I have the same issue.  It seems to happen after a few days of uptime.  Then I can't launch anything until I reboot.  I have no solution yet.

---

### Post by cybermac912 on 2011-06-16
Well, it sounds like the best bet is to go ahead and open up a bug report. Haven't seen it for a couple of days, but I'll open it the next time it happens.

---

### Post by orville99 on 2011-06-17
This is happening to me as well. Very annoying. Any suggestions would be much appreciated.

---

### Post by orville99 on 2011-06-17
After some investigation, I noticed that dbus-daemon was consuming 100% of one of my cpus. Running a strace -p on the dbus-daemon shows that there are too many open files. The internets revealed that this is an issue stemming from kpackagekitsmarticon not closing it's sockets.

short term fix: killall kpackagekitsmarticon
work around: uninstall kpackagekit

The bug has already been logged:

[https://bugs.kde.org/show_bug.cgi?id=261180#c4](https://bugs.kde.org/show_bug.cgi?id=261180#c4)
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/779849](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/779849)

Hope this helps.

---

### Post by logichype on 2011-06-17
short term fix:  killall kpackagekitsmarticon

Yes, that does it!  And the problem description makes sense.  Good work!

---

### Post by cybermac912 on 2011-06-20
Very good. Thanks.

---

### Post by Migrus on 2011-06-20
Thanks, just had this problem too and killing kpackagekitsmarticon solved it (and opened all the windows I had queued up...).

It was a difficult problem to search for. Some terms I used:
application start new window does not appear showing

The patch in the linked KDE bug has been applied to the development trunk (today). Looks like it would apply to kdelibs 4.6.2 as well. It just unregisters what the constructor registered and disconnects from dbus.

Oh, and now the kpackagekitsmarticon icon actually appeared when there was an update. Is something starting and stopping that icon all the time, and each time it leaks a filedescriptor? Should be a fairly common problem unless you restart the computer every day.

---

### Post by ostaja on 2011-06-26
Thanks a lot. This bug was driving me crazy!

BTW, is it safe to uninstall kpackagekit and/or will there be an automatic update which will fix this problem?

---

### Post by cybermac912 on 2011-06-27
> **ostaja said:**
> BTW, is it safe to uninstall kpackagekit and/or will there be an automatic update which will fix this problem?

I think the problem has been patched upstream, but I don't know if the Ubuntu devs will backport it to Natty or wait for Oneiric. In the meantime, I *believe* it's safe to uninstall kpackagekit;  you just won't get auto-notified of updates and will need to do your updates via command line. I may be speaking what I do not know, though ;)

---

