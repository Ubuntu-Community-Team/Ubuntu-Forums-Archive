---
title: "installed Kubuntu desktop and no shutdown or restart in KDE"
date: 2011-03-21
forum: Desktop Environments
---

### Post by burdebc on 2011-03-21
I just recently installed Kubuntu desktop onto Ubuntu and I don't have any shutdown or restart options shown in KDE, but they show up in Gnome.  I initially installed Kubuntu using GDM instead of KDM and switched to KDM when I saw that my Gnome taskbars overlayed my KDE taskbars.  
To switch from GDM to KDM I used the following command:

sudo dpkg-reconfigure gdm

After enabling KDM the terminal suggested a command to configure KDM, however I can't remember the command.  I ran it and I got a message that KDM was already configured.  Any help would be greatly appreciated.

---

### Post by Zorael on 2011-03-21
I'm not sure what you're asking for.

KDE cannot offer shutdown options if you use gdm, simply because gdm developers haven't gone to the extra lengths to make it interoperable with KDE sessions. Recent versions of kdm (4.6) should work with both GNOME and KDE.

Packages are "configured" upon installation, but can be reconfigured with dpkg-reconfigure as you did with gdm. Trying to configure an already configured package will just throw an error, yes.
```
$ sudo dpkg --configure kdm
[sudo] password for zorael: 
dpkg: error processing kdm (--configure):
 package kdm is already installed and configured
Errors were encountered while processing:
 kdm
```

As it is now, is anything not working?

---

### Post by burdebc on 2011-03-21
I don't think you understand what I did, I switched from gdm to kdm and lost my buttons in the switch, but no matter, they showed back up after I restarted.  I thought logging out would refresh everything, but it didn't.

---

