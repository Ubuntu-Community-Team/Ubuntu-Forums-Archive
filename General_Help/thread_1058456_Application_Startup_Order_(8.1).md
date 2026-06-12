---
title: "Application Startup Order (8.1)"
date: 2009-02-02
forum: General Help
---

### Post by njsanders1 on 2009-02-02
I'm trying to find out two things about the startup process in 8.10.  First, I'd like to see a general primer on the startup process of an Ubuntu system (from GRUB to Gnome/KDE), including references to config files and such that contribute to and control the tasks comprising the process.  Second, I'd really like to know (and this is the question that prompted me to post in the first place) how to change the startup order for those apps I have selected to run on startup.  I've found tutorials for previous builds of Ubuntu, and they refer to a capability found in the "Sessions" app under System/Preferences; however, the option to change the order of the apps isn't there in 8.1 -- they're listed alphabetically. 

Any help would be appreciated, and references to other versions (i.e., *not* 8.1) that derail the original questions will **NOT** be appreciated.  :p

Thanks in advance...

---

### Post by Roger N on 2009-02-03
I second that request - one of my problems as detailed in another post is that even though I change the session type at the log in screen 8.10 still always brings up Gnome. Have proved that Xfce is there as can change session type manually by typing into a terminal.  Without knowing what should be happening it is difficult to find were the fault is.

---

### Post by eotakos on 2009-02-03
the prosseses mentioned at the "sessions preferences" - startup programs are executed momentarity after your login. A usefull tool for the system processes is the boot up manager, aka bum.

check this link out - it explains the basics

[http://www.marzocca.net/linux/bumdocs.html#order](http://www.marzocca.net/linux/bumdocs.html#order)


in a nutshell, the boot up order goes like this:

a) execute things in the /etc/rcS.d
b) execute things in the /etc/rc2.d  (this is if you haven't changed the runlevel


by saying "things" i mean: in these folders execute the scripts starting with S (with the order of the numbers embeded in the file-names) - the scripts starting with K aren't executed.

the /etc/rc.local is executed last (see the /etc/rc2.d folder).

if you'd like to add programs in the startup order you can add scripts in the /etc/init.d folder and recall them from within the /etc/rc.local file


that's my experience until now...  any corrections or additions are wanted and welcome! :-)


edit: 
i'm running 8.04, but this things are way too basic to be changed over a dist-upgrade. the process i described is like of debian origin - like ubuntu --

---

### Post by njsanders1 on 2009-02-03
Thanks for the info -- that's a good start.  However, I have loaded and gone through all of the information in BUM, but I don't see anything related to the apps I have starting automatically as defined in "Sessions."  For example, I have Tomboy and Skype starting on boot, as well as a few Screenlets.  I don't see these apps listed anywhere in BUM.  Where is that information stored?

---

### Post by mcduck on 2009-02-03
> **njsanders1 said:**
> Thanks for the info -- that's a good start.  However, I have loaded and gone through all of the information in BUM, but I don't see anything related to the apps I have starting automatically as defined in "Sessions."  For example, I have Tomboy and Skype starting on boot, as well as a few Screenlets.  I don't see these apps listed anywhere in BUM.  Where is that information stored?

They are not started at boot, but at login time. ;)

BUM manages system boot process, Sessions manages your personal desktop session. (programs in your session are started by gnome-session-manager which, if I remember right, stores it's configuration in gconf.)

By the way, the boot process as described in eotakoses post is becoming history, and Ubuntu is moving from old runlevel-based system to event-based system. This means that instead of defining certain pre-configured runlevels and services that should be running on each runlevel different services will be started based on system events. For example the old way would tell that networking and firewall should be started on certain runlevel. The event-based system would be that when network services are started when user wants to connect to a network, and firewall is started when network connection is activated. Or drivers for USB webcam are loaded when such  device is connected, instead of always loading them on some pre-defined runlevel.. Currently only parts of the system work this way, and the rest is still started using the old system. In the future upstart will handle everything.

[http://upstart.ubuntu.com/]("http://upstart.ubuntu.com/")

---

### Post by cariboo on 2009-02-03
You can view what happens at startup by either opening an Applcations-->Accessories-->Terminal and type:

```
dmesg | less
```

using less you can use the space bar to scroll the text. Or go to System-->Administration-->Log File Viewer and select messages.

Jim

Edit: the files you are looking for are in ~/.config.  To view the files open Nuatilus (Places-->Home Folder) and press Ctrl-h to view hidden files and directories.

---

### Post by eotakos on 2009-02-03
this is where i thank mcduck for the information i had no idea about. 

i'm new to ubuntu and i find pleasure in learning how stuff works and also in catching up with the OS's evolution. :-)

---

### Post by njsanders1 on 2009-02-03
.

---

### Post by njsanders1 on 2009-02-03
> **cariboo907 said:**
> You can view what happens at startup by either opening an Applcations-->Accessories-->Terminal and type:

```
dmesg | less
```using less you can use the space bar to scroll the text. Or go to System-->Administration-->Log File Viewer and select messages.

Jim

Edit: the files you are looking for are in ~/.config.  To view the files open Nuatilus (Places-->Home Folder) and press Ctrl-h to view hidden files and directories.

Jim,
What defines the starting order for the apps listed in ~/.config/autostart?  Is it alphabetical?  If that's true, would there be undesirable results if I renamed these files (i.e., like putting a numeric in front of the files, like in the rcX directories)?

Nick

---

