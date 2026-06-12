---
title: "Need to file bug about gnome-time-admin, but don't know where..."
date: 2013-11-25
forum: Desktop Environments
---

### Post by scott092707 on 2013-11-25
When I use gnome's time-admin (terminal, or SystemTools-->Time-and-date), it has the option to either "Keep synchronized with Internet servers" (default) or "Manual".  In the past (Ubuntu 9.10) it gave the ability to see the list of servers, and select which one(s) I wanted to use.  (I was in Germany at the time, and I had to change the server because the default one for my location was non-functional).

Now, that ability is no longer there.  [When was it removed?]

YET, when one clicks on Help, the documentation that pops up shows a button to click, in order to show the servers, and doing so shows the window where the servers are displayed and one can select one or more by checkmarking.
Gnome's online help page for this ([https://help.gnome.org/users/time-admin/stable/](https://help.gnome.org/users/time-admin/stable/)) shows the same thing.

Some searching showed me that the program was time-admin, in the gnome-time-admin package.  There appears to be a relationship with gnome-system-tools...

I tried to find "gnome-time-admin" or "gnome-system-tools" at gnome's bug-list site ([https://bugzilla.gnome.org/enter_bug.cgi?classification=__all](https://bugzilla.gnome.org/enter_bug.cgi?classification=__all)), but they are not listed.
I entered the bug under gnome-control-center/time-and-date (which seemed the most likely place), but the reponder said it never had the ability to show/change the internet time servers, and this was apparently therefore not the right place to file the bug.
I cannot find the right place to file the bug with gnome, so I am trying to get help here.

I was surprised to find that the Gnome Project Listing ([https://projects.gnome.org/](https://projects.gnome.org/)) lists gnome system tools, but the ftp page has the last version (3.0 - the version on my Lubuntu 13.10 distro) as being from  2011-04-03, two and a half years ago.  Perhaps it is no longer being developed...?
(The project listing page has a copyright of "Copyright © 2005-**2009** [The GNOME Project]("http://www.gnome.org/")."), so one wonders if that page _itself_ may no longer be valid...)

Anyway...

1) Even if time-admin is no longer being developed, then if the ability to see/change the internet time servers was removed, then the help screens/web help pages should reflect that change.
**Where**, therefore should I report the "bug", since where I did so was the wrong place?

2) Since [L]ubuntu **is** apparently using internet time servers to keep the correct time (unless one switches to manual mode), then it seems only logical that one should have the ability to see what servers are being used, and change them, in case of problems.  Is there another program currently on my system that does give that ability, that I have not managed to find? If not, what other program does?
It seems to me that removing that ability from time-admin is a regression...

3) If the current gnome-system-tools is so old, shouldn't [L]ubuntu have found something more current for the task(s), that is still being maintained?
[I suppose, upon reflection, that perhaps gnome changed its system entirely, and that the project list and ftp for gnome-system-tools, are not the current places for looking at current gnome projects and the (possibly still current) gnome-system-tools...  **But**, if so, wouldn't the version number have changed in two and a half years...?]

If someone has any insight and answers to the above questions, I would be very grateful to read them.

-Scott

I have attached screenshots showing time-admin's help windows, that show the button that one can click to select time servers, and the window that results from that click showing various internet time servers which one can checkmark to select.

----------------------------------
scott@scott-ASUS-M2N68-AM-PLUS:~$ uname -a
Linux scott-ASUS-M2N68-AM-PLUS 3.11.0-13-generic-tuxonice #20~ppa1-Ubuntu SMP Fri Nov 8 11:40:45 UTC 2013 i686 athlon i686 GNU/Linux

scott@scott-ASUS-M2N68-AM-PLUS:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
[Actually _Lubuntu_]  (is there a terminal command that shows "Lubuntu" (or "Kubuntu", or ...) ? )

gnome-time-admin      : 3.0.0-2ubuntu2
gnome-system-tools    : 3.0.0-2ubuntu2
system-tools-backends : 2.10.2-1ubuntu1
liboobs-1-5                 : 3.0.0-1

---

### Post by bashiergui on 2013-11-26
See this page which details how to file a bug in Ubuntu.
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by ian-weisser on 2013-11-26
I agree with the OP that the documentation issue should be upstreamed to the Gnome bug tracker. Letting it get stale on Launchpad or Debian bug trackers won't help anybody, and just makes more (needless) work for volunteer triagers.
Best place to ask which Gnome product to associate with is probably on Gnome's IRC: irc://irc.gnome.org/bugs

I disagree that removing the GUI ability to view/change the timeservers is a regression. It was a deliberate elimination. Unskilled users were forever using awful servers, or the wrong stratum, then complaining about the consequences ("Why is my system 10 minutes off?"). This forum used to have a *lot* of those, years ago. To replace the user-selection, Ubuntu (and Gnome, and others) use a pool system that automatically excludes outlier members...and an entire class of complaints and support requests vanished. I don't miss them. A classic case of making the system smarter so it need not pester the user.

As I'm sure you already know, you can still edit the NTP servers all you wish. They are in the /etc/ntp.conf file. Including the ability to prioritize your own servers ahead of the (fallback) pool.

There's really not much need for time-admin to increment much. It doesn't do much, but it does the job well and reliably.

---

### Post by scott092707 on 2013-11-26
Well, I asked on irc://irc.gnome.org/bugs (never IRC'd before; installed xChat and eventually figured out what to do...), and it was suggested that it might be part of gnome-settings-daemon.
I DO have gnome-settings-daemon (in my Lubuntu 13.10), and I googled that term and time-admin together, and came up with a launchpad bug report, so that is probably right.  It was also suggested that I file the bug first with my distribution, so I will find where to do that, and then also probably file it with gnome.

---

### Post by ian-weisser on 2013-11-26
I think gnome-system-tools more than gnome-settings-daemon. Time settings are not related to gsettings. The 'setting' term may be confusing them.

Your distribution's bug tracker is at launchpad.net.
For gnome-time-admin, use [https://launchpad.net/ubuntu/+source/gnome-system-tools/+filebug](https://launchpad.net/ubuntu/+source/gnome-system-tools/+filebug)

The launchpad bug report has a field along the right-hand column to (later) enter the Gnome bug number. Launchpad will track the Gnome bug.

---

