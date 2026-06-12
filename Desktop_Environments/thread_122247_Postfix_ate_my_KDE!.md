---
title: "Postfix ate my KDE!"
date: 2006-01-27
forum: Desktop Environments
---

### Post by GnuSense on 2006-01-27
I resisted the urge to upgrade to Breezy since it was released, but the day before yesteday I figured most of the bugs must have been worked out and decided to take the plunge.  OK, some folks are just too dumb to run Linux, next issue.  I mean why fix something that isn't really broken just because someone issues a new release?  

Anywho, it seemed like some folks were able to upgrade by merely switching every incidence of hoary to breezy in the sources.list, so I vi'ed the file and issued the command:
[CENTER]:%s/hoary/breezy/g[/CENTER]

I dropped to a console and did an apt-get update, then apt-get dist-upgrade.  It downloaded all night and in the morning gave me a bunch of errors and refused to boot in to X.  I got some message stating  that a necessary font wasn't where it was expected (I should have saved the xorg log, but didn't).

I tried mucking with a few 'sources.list's that I found on the net and even tried adding 'deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main' hoping that if I shoveled enough manure on my drive something beautiful would grow (and actually, getting 3.5 was the main reason I upgraded Hoary; it didn't seem to be supported for the older version).

No joy, then I tripped over a page that I could swear was down when I tried to look at it before upgrading.  
[CENTER][https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)[/CENTER]

Anyway, it suggested that before trying to upgrade I should do a:
[CENTER]apt-get remove firefox mozilla-firefox[/CENTER]
And then:
[CENTER]apt-get install mozilla-firefox[/CENTER]
And then:
[CENTER]apt-get install ubuntu-base ubuntu-desktop[/CENTER]

Well, I did the first two steps, and saw a bunch of activity, including registering a ton of fonts.  I tried installing ubuntu-base & desktop and got some messages which I misrember, but in any case, when I tried 'startx' I was able to boot, but in to the dreaded Gnome desktop.  Attempts to execute 'startkde' were to no avail.  I get the following error messages and remain in a console. 


[INDENT]startkde
xsetroot:  unable to open display ''
xset:  unable to open display ""
xsetroot:  unable to open display ''
startkde: Starting up...
ksplash: cannot connect to X server 
kdeinit: Aborting. $DISPLAY is not set.
Warning: connect() failed: : No such file or directory
ksmserver: cannot connect to X server 
ERROR: Couldn't attach to DCOP server!
startkde: Shutting down...
Warning: connect() failed: : No such file or directory
Error: Can't contact kdeinit!
startkde: Running shutdown scripts...
startkde: Done.[/INDENT] 

I booted back to Gnome and noticed that my email and IM settings, etc., were gone.  Very bad news, time to start over, until I noticed I'd booted X as root after doing a 'sudo -s -H' to save time while mucking around.  I didn't think (x)Buntu allowed GUI root logins, so I obviously borked something.

Well, I am back on "K"Ubuntu in my regular account and have lots of KDE apts (like kynaptic, Konqueror 3.5, etc.), but can't boot in to KDE (and I really don't like Gnome).  Plus, there are obviously some weird ticks, like not being able to switch directories to change icons in the Panel, so Gnome, which never impressed me, seems even less inviting.  

Any attempt to 'apt-get' much of anything, including 'update' gets me something like this:

[INDENT][SIZE="1"]# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  libfaac0
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up postfix (2.2.4-1ubuntu2) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent...                                     postfix/postfix-script: fatal: the Postfix mail system is already running
                                                                         [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core; however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-cxx; however:
  Package lsb-cxx is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/SIZE][/INDENT]

So forget about getting Fluxbox or XFCE, much less KDE.

Anybody have any idea what this gibberish means or what I might be able to do about it?  Otherwise, I'm afraid I'll just have to live with Gnome Breezy (with a couple of things broken) until I work up the gumption to format my root partiton and start over (probably some time around the middle of April) after backing up a few of my /etc files.  Or (Dog forbid) install something else (the newly released Vector SOHO springs to mind...)

---

### Post by GnuSense on 2006-01-27
Oh, before someone suggests running:

[INDENT]dpkg-reconfigure xserver-xorg[/INDENT]

I did, and it didn't seem to help for some reason.  I'm sure it was something I did in a past life.

---

### Post by redondos on 2006-02-18
I just had the exact same problem: installing postfix broke kde 3.5.1 from the Breezy repositories.

I can still run KDE from a console with:
X :0 & DISPLAY=:0; startkde

Did you manage to fix the problem? If so, please enlighten me.

Cheers!
--
redondos

---

### Post by redondos on 2006-02-19
My problem seemed to be related to the / partition being screwed up. A fsck 
fixed it, hopefully not momentarily. I found out what went wrong when trying 
to reinstall dbus: the partition was mounted read-only! But that happened 
during the last of many reboots the system had while I was trying to solve 
the problem.

--
redondos

---

### Post by GnuSense on 2006-02-19
Actually, I just removed the Postfix package and some other package that was irritated at me and then did an 'apt-get upgrade', I believe, and I was able to get  boot to KDE.  It has been a couple of weeks and I'm on another box, so I forget all the gruesome details.

---

