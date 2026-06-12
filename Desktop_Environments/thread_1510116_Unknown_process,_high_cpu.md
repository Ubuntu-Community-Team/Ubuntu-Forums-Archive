---
title: "Unknown process, high cpu"
date: 2010-06-15
forum: Desktop Environments
---

### Post by JoakimP on 2010-06-15
I have the UNE 10.04 installed on a Asys 900. I have a problem with a unknown process running and eating CPU. If I look in the System monitor It shows a process with no apparent parent being started. It terminates and another one starts. Since it slows my system down I cannot get hold of the process before it terminates to see what it is or where it comes from. 

This happens basically each time I start the system. If I start it in Gnome it does not happen so I think it has something with UNE to do. Any ideas anyone?

---

### Post by mikewhatever on 2010-06-15
Have you tried running **top**? It automatically puts the cpu intensive processes at the top of the list. The netbook edition is basically Gnome with a few added packages.

---

### Post by nischalinn on 2010-06-15
try the  "**top**". It lists all the processes running and then you can kill the process via **sudo kill pid.**

---

### Post by JoakimP on 2010-06-15
I have tried top, but the process spawns a new process and then dies quicker than I can kill it. The new process does the same and so on and so on. This process of spawning and dying is what takes CPU.

---

### Post by mikewhatever on 2010-06-15
Killing the process wasn't the point. Can you tell what its name is?

---

### Post by JoakimP on 2010-06-15
I see now that it is nautilus. It does not act that way if I start it in Gnome.
In **top** I can see nautilus, but in the System monitor is is unnamed, has no command line and no marking for memory.

---

### Post by JoakimP on 2010-06-16
Update: I tried to disable CIFS volumes in fstab. It didn't help! I also tried all different desktops (UNE3d, 2d, Gnome and Failsafe Gnome) The only one where I do not have this problem is in Failsafe Gnome. Does anyone know how it differs from normal Gnome? What is not started?

Any ideas on how to follow the startup process step by step? Or which log to look in for this problem? We are travelling to the US in a few days and wanted the Asus for games and films.

---

### Post by joshmuffin on 2010-06-16
Nautilus is the file browser

---

### Post by JoakimP on 2010-06-16
> **joshmuffin said:**
> Nautilus is the file browser

I know. Still it spawns multiple instances of itself and dies. No GUI is shown either. In the lower panel it shows multiple "Starting file manager". I have traced this to be and old error. It could have something to do with the X-server and I might need to change the xorg.conf file, but is isn't there anymore in Lucid :(

---

### Post by JoakimP on 2010-06-16
I found a post in another forum :-? that solved the issue. 
[http://bbs.archlinux.org/viewtopic.php?id=69282]("http://bbs.archlinux.org/viewtopic.php?id=69282")
It seems that it is a configuration issue in nautilus.

Anyway, thanks for the help.

---

### Post by JoakimP on 2010-08-02
The error reappeared yesterday,after a system update. Probably a major change which included a new setup of nautilus configurations. These configurations are the root of my problem. The same fix as above solved the issue again. In short I did the following changes:

Edit the /usr/share/applications/nautilus.desktop file.  The edits made are:
```
X-GNOME-AutoRestart=false    # changed from =true
AutostartCondition=GNOME /apps/nautilus/preferences/show_desktop    # added this line
```

Restart the system

---

### Post by Protocol84 on 2010-10-01
I have tried all of the solutions here and none have worked yet. Every time I start up Nautilus is open and I have un-named processes changing ID's very fast, I cannot see these processes in top, only system monitor can see them. 

this post :[https://bbs.archlinux.org/viewtopic.php?id=69282](https://bbs.archlinux.org/viewtopic.php?id=69282)

States "Put dbus in DAEMONS in /etc/rc.conf. You might want to add hal also."

I have no /etc/rc.conf 

it also states: 
I just commented out this line in xorg.conf, like this 
Section "ServerFlags"  # Option "AllowEmptyInput" "false"  Option "DontZap"   "false"  EndSection

I do not have those lines in my xorg.conf so I am rather lost as to how I fix this.

Oh I am running 10.04

---

### Post by JoakimP on 2010-10-01
I did not do anything else but the changes in /usr/share/applications/nautilus.desktop I mentioned, and restared the computer (partly because the other files don't exist in 10.04..). This solved the issue for me.

Have you done any other changes except these?

I have tried to look for a bug report of this in Launchpad but with no success. I'll try to see if I can find any more info somewhere.

---

