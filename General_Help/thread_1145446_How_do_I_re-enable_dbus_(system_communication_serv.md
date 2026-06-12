---
title: "How do I re-enable dbus (system communication service)?"
date: 2009-05-01
forum: General Help
---

### Post by miked2 on 2009-05-01
Hello there Ubuntu people.  Don't do this:

Been using Jaunty Jackalope for the last day or so.  Everything was working perfectly until...
In a moment of madness earlier this evening I selected System - Administration - Services and deselected the system communication service.  
Some three hours later I'm still trying to find a way of enabling it again without the benefit of a graphical interface.  
I did find someone else [[COLOR="DarkRed"]here[/COLOR] ]("http://ubuntuforums.org/archive/index.php/t-289654.html") that did the same thing, but their solution doesn't work for me.  
I booted in recovery mode, dropped back to root shell & tried 
```
/etc/init.d/dbus start
```
& that did work:
```
* Starting system message bus dbus  [OK]
```
then I tried 
```
startx
```
after which the gnome desktop starts to load, but then quits with a message popup announcing:
Error "user switcher" has quit unexpectedly
the mouse & keyboard are unresponsive.  
I've also tried 
```
services-admin
```
from the root terminal after starting dbus, but this gives:
```
Gtd-WARNING  **: cannot open display
```
What I need is a way to re-enable the system communication bus from the root shell.  
Any suggestions would be much appreciated.

---

### Post by buchan on 2009-05-01
If you removed dbus from your startup services you should be able to re-enable it by staring up normally logging in at the cmd prompt and typing the following:

```

sudo update-rc.d -f dbus defaults
```

You should see something like this after the command is entered:
```
/etc/rc0.d/K20hobbit-client
   /etc/rc1.d/K12dbus
   /etc/rc2.d/S12dbus
   /etc/rc3.d/S12dbus
   /etc/rc4.d/S12dbus
   /etc/rc5.d/S12dbus
   /etc/rc6.d/K12dbus
```

I think this is what your after, the simple way to check to see if the dbus service is enabled is to look in /etc/rc3.d and see if there is a shortcut to the service

type: 
```

ls -l /etc/rc3.d
```

and somewhere in the list you should see this if the service is enabled at startup:

```

S12dbus -> ../init.d/dbus*
```

Hope this helps...

---

### Post by miked2 on 2009-05-02
Thanks for the suggestion buchan. 
I tried resetting dbus defaults as you suggested & got:
```
System startup links for /etc/init.d/dbus already exist
```
I do have the S12dbus link in /etc/rc3.d that links to the dbus script in init.d.  The dbus script is unmodified.  
Could a manual start of dbus that I tried earlier have restored the S12dbus script maybe?
I did try earlier to run xfix from the recovery startup screen.  I'm wondering now whether there's a way to verify that dbus is starting up correctly?  
....
(pausing for thought)
...
I read the README in rc3.d & that got me looking through the other rcx.d directories.  If I've got this right, links beginning K kill the linked-to service & those beginning S start it.  Should gdm be shutdown in run level 6?  Is there anything suspicious here?
```
/etc/rc6.d:
K01gdm               K74bluetooth                        S30urandom
K02usplash           K86avahi-daemon                     S31umountnfs.sh
K20apmd              K99laptop-mode                      S35networking
K20apport            README                              S40umountfs
K39ufw               S01linux-restricted-modules-common  S60umountroot
K50alsa-utils        S15wpa-ifupdown                     S89casper
K63mountoverflowtmp  S20sendsigs                         S90reboot

```

Thanks again.

---

### Post by raronson on 2009-07-06
I ran into the same problem, and it appears that suggestions for how to fix this vary according to release (though I could be wrong).

Short description of the problem
-------------------------------------
In Jaunty (9.04) within Gnome, if you go to:

System --> Administration --> Services (which is the application 'services-admin')

And disable 'System Communication Bus (dbus)', then the dbus link for the runlevel 2 (/etc/rc2.d, which starts up the normal graphical environment), 'S12dbus' gets deleted.

You fix this by booting into recovery mode, selecting 'root', and entering the following command:

```
ln -s /etc/init.d/dbus /etc/rc2.d/S12dbus
```Reboot...

If you have questions, ask.  I've read posts where people have reinstalled over this problem.  In Linux, there's usually never a need to do that.

---

### Post by mdh on 2009-07-31
Awesome! Creating the above link did the trick for me. Thanks!

---

### Post by miles916 on 2009-09-24
thank you so much!

---

### Post by vmidhun09@gmail.com on 2009-11-16
[Raronson]("http://ubuntuforums.org/member.php?u=867852") .... dude.. you saved ma life too... i played with System service in ma office server.. Thanks alot...

---

### Post by Paolohn on 2011-07-12
How about 10.04 (lucid) ? I need to enable dbus so I that my Guest OS [XP] can access USB devices!

---

