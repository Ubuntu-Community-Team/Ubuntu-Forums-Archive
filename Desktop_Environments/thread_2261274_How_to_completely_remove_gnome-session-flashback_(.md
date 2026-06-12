---
title: "How to completely remove gnome-session-flashback (any software)"
date: 2015-01-17
forum: Desktop Environments
---

### Post by newbie13 on 2015-01-17
Installed gnome-session-flashback using

```
sudo apt-get install gnome-session-flashback
```

It said 10mb will be downloaded and 50mb disc space will be used after install. I checked this in software center too. Same thing was shown there.

I liked the gnome for not having launcher and that dropdown menu which is far better, for me, than unity launcher and dash. But one thing I couldn't compromise was no integration of the upper most bar in ubuntu and file menu. Unity is my first DE so I have got used closing windows by taking cursor to the far most point in upper left corner and clicking without worrying about if the cursor is on the cross or not. So I decided to remove it. But when I give command

```
sudo apt-get remove gnome-session-flashback 
``` 

It says only 289kb disc space will be freed, if I use autoremove then it says 276mb will be freed. And if I use software center then it shows 289kb will be freed.

So I am confused how to remove gnome completely without hurting anything else.

---

### Post by egeezer on 2015-01-17
To really clean out a package: 

```
sudo apt-get remove –purge (package name)]
```

[That's a double dash before the word purge]  

And if you like drop-down menus and are launcher-averse (like me!) try the Xfce desktop.  To do it right and get all the advantages of the unparalleled configurability of Xfce, use

```
sudo apt-get install xfce4 xfce4-goodies
```  

The goodies let you manipulate practically every aspect of the desktop control.

---

### Post by zombifier25 on 2015-01-18
Actually, purge will only additionally clean out the configuration files, which would most likely not take up any significant megabytes.

To OP, the reason is that when you install gnome-panel, you're also installing all of its depedencies (if you did not use the --no-install-recommends flag, then it will also pull in a lot of extra "recommended" packages, such as gnome-shell, evolution and the like). When you remove gnome-panel, you're only removing it, not all the packages that come with it. They will instead be marked as redundant and will be removed if you do a sudo apt-get autoremove.

Still, to be extra careful, please post the list of packages that autoremove will remove.

---

### Post by newbie13 on 2015-01-18
no success with '--purge'
```
ajinkya@Ajinkya-ubuntu:~$ sudo apt-get remove --purge gnome-session-flashbackReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-39 linux-headers-3.13.0-39-generic
  linux-image-3.13.0-39-generic linux-image-extra-3.13.0-39-generic
  linux-signed-image-3.13.0-39-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnome-session-flashback*
0 upgraded, 0 newly installed, 1 to remove and 31 not upgraded.
After this operation, 289 kB disk space will be freed.



```

list of packages that will autoremove remove
```
ajinkya@Ajinkya-ubuntu:~$ sudo apt-get autoremove gnome-session-flashbackReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-session-flashback linux-headers-3.13.0-39
  linux-headers-3.13.0-39-generic linux-image-3.13.0-39-generic
  linux-image-extra-3.13.0-39-generic linux-signed-image-3.13.0-39-generic
0 upgraded, 0 newly installed, 6 to remove and 31 not upgraded.
After this operation, 271 MB disk space will be freed.



```

As far as I know, those linux images are kernels, right? I don't want to uninstall them because in case I get into a problem then using older kernel would be one of the suggestions. But if you say there is no harm in removing it then I will do it.

---

### Post by kansasnoob on 2015-01-18
From what I'd written [here]("http://ubuntuforums.org/showthread.php?t=2184682&page=38&p=12986315#post12986315") I think this should work (notice that I've added -s to the end of that command so it only simulates what would be done - if it appears to NOT break anything simply repeat without the -s):

```
sudo apt-get purge alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-control-center gnome-control-center-data gnome-media gnome-panel gnome-panel-data gnome-session gnome-session-flashback gnome-settings-daemon gstreamer0.10-gconf indicator-applet-complete libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 libpanel-applet-4-0 metacity notification-daemon -s
```

Testing it here looks OK:

```
lance@lance-desktop:~$ sudo apt-get purge alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-control-center gnome-control-center-data gnome-media gnome-panel gnome-panel-data gnome-session gnome-session-flashback gnome-settings-daemon gstreamer0.10-gconf indicator-applet-complete libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 libpanel-applet-4-0 metacity notification-daemon -s
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B][COLOR="#FF0000"]The following packages were automatically installed and are no longer required:
  hddtemp libsensors-applet-plugin0
Use 'apt-get autoremove' to remove them.[/COLOR][/B]
The following packages will be REMOVED:
  alacarte* gir1.2-gconf-2.0* gir1.2-panelapplet-4.0* gnome-applets*
  gnome-applets-data* gnome-control-center* gnome-control-center-data*
  gnome-media* gnome-panel* gnome-panel-data* gnome-session*
  gnome-session-flashback* gnome-settings-daemon* gstreamer0.10-gconf*
  indicator-applet* indicator-applet-complete* libgnome-media-profiles-3.0-0*
  libgoa-backend-1.0-1* libpanel-applet-4-0* metacity* notification-daemon*
  sensors-applet* shiki-colors-metacity-theme*
0 upgraded, 0 newly installed, 23 to remove and 2 not upgraded.
Purg alacarte [3.10.0-1ubuntu2]
Purg gnome-applets [3.5.92-0ubuntu3]
Purg gir1.2-panelapplet-4.0 [1:3.8.0-1ubuntu12.2]
Purg gir1.2-gconf-2.0 [3.2.6-0ubuntu2]
Purg gnome-applets-data [3.5.92-0ubuntu3]
Purg gnome-control-center [1:3.6.3-0ubuntu56.1]
Purg gnome-control-center-data [1:3.6.3-0ubuntu56.1]
Purg gnome-media [3.4.0-1ubuntu2]
Purg gnome-session-flashback [1:3.8.0-1ubuntu12.2]
Purg gnome-panel [1:3.8.0-1ubuntu12.2]
Purg gnome-panel-data [1:3.8.0-1ubuntu12.2]
Purg gnome-session [3.9.90-0ubuntu12]
Purg gnome-settings-daemon [3.8.6.1-0ubuntu11.2]
Purg gstreamer0.10-gconf [0.10.31-3+nmu1ubuntu5]
Purg indicator-applet [12.10.2+14.04.20140403-0ubuntu1]
Purg indicator-applet-complete [12.10.2+14.04.20140403-0ubuntu1]
Purg libgnome-media-profiles-3.0-0 [3.0.0-1ubuntu2]
Purg libgoa-backend-1.0-1 [3.10.3-0ubuntu1]
Purg sensors-applet [3.0.0+git4-2ubuntu2]
Purg libpanel-applet-4-0 [1:3.8.0-1ubuntu12.2]
Purg shiki-colors-metacity-theme [4.6-1ubuntu2]
Purg metacity [1:2.34.13-0ubuntu4]
Purg notification-daemon [0.7.6-1]

```

Take notice of the highlighted part where it orphans two packages related to 'sensors-applet'.

Just to be on the safe side when that completes (without the -s) I'd recommend running:

```
sudo apt-get install ubuntu-desktop
```

That should hopefully ensure that you've not broken the Unity DE.

---

### Post by newbie13 on 2015-01-18
This is what I get
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package 'gnome-session' is not installed, so not removed
[COLOR=#ff0000]The following packages were automatically installed and are no longer required:[/COLOR]
[COLOR=#ff0000]  linux-headers-3.13.0-39 linux-headers-3.13.0-39-generic[/COLOR]
[COLOR=#ff0000]  linux-image-3.13.0-39-generic linux-image-extra-3.13.0-39-generic[/COLOR]
[COLOR=#ff0000]  linux-signed-image-3.13.0-39-generic[/COLOR]
[COLOR=#ff0000]Use 'apt-get autoremove' to remove them.[/COLOR]
The following packages will be REMOVED:
  alacarte* gir1.2-gconf-2.0* gir1.2-panelapplet-4.0* gnome-applets*
  gnome-applets-data* gnome-control-center* gnome-control-center-data*
  gnome-media* gnome-panel* gnome-panel-data* gnome-session-flashback*
  gnome-settings-daemon* gstreamer0.10-gconf* indicator-applet-complete*
  libgnome-media-profiles-3.0-0* libgoa-backend-1.0-1* libpanel-applet-4-0*
  metacity* notification-daemon*
0 upgraded, 0 newly installed, 19 to remove and 31 not upgraded.
Purg alacarte [3.10.0-1ubuntu2]
Purg gnome-applets [3.5.92-0ubuntu3]
Purg gir1.2-panelapplet-4.0 [1:3.8.0-1ubuntu12.2]
Purg gir1.2-gconf-2.0 [3.2.6-0ubuntu2]
Purg gnome-applets-data [3.5.92-0ubuntu3]
Purg gnome-control-center [1:3.6.3-0ubuntu56.1]
Purg gnome-control-center-data [1:3.6.3-0ubuntu56.1]
Purg gnome-media [3.4.0-1ubuntu2]
Purg gnome-session-flashback [1:3.8.0-1ubuntu12.2]
Purg gnome-panel [1:3.8.0-1ubuntu12.2]
Purg gnome-panel-data [1:3.8.0-1ubuntu12.2]
Purg gnome-settings-daemon [3.8.6.1-0ubuntu11.2]
Purg gstreamer0.10-gconf [0.10.31-3+nmu1ubuntu5]
Purg indicator-applet-complete [12.10.2+14.04.20140403-0ubuntu1]
Purg libgnome-media-profiles-3.0-0 [3.0.0-1ubuntu2]
Purg libgoa-backend-1.0-1 [3.10.3-0ubuntu1]
Purg libpanel-applet-4-0 [1:3.8.0-1ubuntu12.2]
Purg metacity [1:2.34.13-0ubuntu4]
Purg notification-daemon [0.7.6-1]
```

To be honest, I am little bit scared about this. If you say removing linux images is okay then I am ready to do autoremove.

---

### Post by deadflowr on 2015-01-18
The output for those linux-image packages is separate from what will happen when you do the gnome-flashback removal.
Those will only be removed if you instigate the autoremove command.

Notice that in the purg output, there is no mention of those kernels.

Anyway, you'd only be removing one kernel (3.13.0-39) which is a little old now, so I doubt you're still using it.
You can double check that it's not the kernel in use, for your own peace of mind, by running
uname -r

I say for your own peace of mind because you would have had to have done something terribly wrong for the system to want to remove the working kernel.

---

### Post by kansasnoob on 2015-01-18
> **deadflowr said:**
> The output for those linux-image packages is separate from what will happen when you do the gnome-flashback removal.
Those will only be removed if you instigate the autoremove command.

Notice that in the purg output, there is no mention of those kernels.

Anyway, you'd only be removing one kernel (3.13.0-39) which is a little old now, so I doubt you're still using it.
You can double check that it's not the kernel in use, for your own peace of mind, by running
uname -r

I say for your own peace of mind because you would have had to have done something terribly wrong for the system to want to remove the working kernel.

+1!

---

### Post by newbie13 on 2015-01-18
> **deadflowr said:**
> 
I say for your own peace of mind because you would have had to have done something terribly wrong for the system to want to remove the working kernel.

Haha... No, I generally do not take risks. My current kernel version is 3.13.0-43, so I am using autoremove. 

If I had used autoremove before all this happened, then, after using autoremove to remove gnome session, would it have shown 50mb will be freed? 
(Don't know if that is correct english. Try to understand what I want to say)

Thank you.. :KS

---

### Post by deadflowr on 2015-01-18
> **newbie13 said:**
> Haha... No, I generally do not take risks. My current kernel version is 3.13.0-43, so I am using autoremove. 

If I had used autoremove before all this happened, then, after using autoremove to remove gnome session, would it have shown 50mb will be freed? 
(Don't know if that is correct english. Try to understand what I want to say)

Thank you.. :KS

Yes.
The output from autoremove  was calculated separately from what the output for the remove/purge/whatever-the-command was to remove the gnome-flashback packages is/was.
autoremove is a different command, and was only showing you extra things you can do, beside removing the packages you listed to be removed.

It was sort of saying, Hey while you are removing all of those (gnome-flashback)packages, these other packages are no longer needed and can also be removed, if you wish.
If that makes any sense...

---

### Post by newbie13 on 2015-01-19
> **deadflowr said:**
> 
It was sort of saying, Hey while you are removing all of those (gnome-flashback)packages, these other packages are no longer needed and can also be removed, if you wish.
If that makes any sense...

This absolutely makes sense for people like me..

@[COLOR=#000000]kansasnoob sorry, I realized it now that you must have put time in creating that command and I simply used autoremove instead. It was showing many packages will be removed so I was a little bit scared. 

[/COLOR]

---

