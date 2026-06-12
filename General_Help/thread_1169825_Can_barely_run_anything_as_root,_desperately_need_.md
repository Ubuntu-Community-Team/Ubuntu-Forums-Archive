---
title: "Can barely run anything as root, desperately need help."
date: 2009-05-25
forum: General Help
---

### Post by ALIENDUDE5300 on 2009-05-25
Ok, this just started today after trying to install an apache server on my Ubuntu desktop as a sort of "sandbox" for me to play around with web code while not actually uploading anything to a real web server. I also set up php5. Now when I try to run just about anything as root, I get really weird errors relating to gconf. Here is a log of some commands I tried to run:
```
dylan@DYLANTAYLOR-PC:~$ sudo gedit
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-nOrcHJ3r6z: Connection refused)
^C
dylan@DYLANTAYLOR-PC:~$ sudo nautilus

(nautilus:30470): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-1mRuy2JLOi: Connection refused)

(nautilus:30470): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-f96DGyfkY8: Connection refused)

(nautilus:30470): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-6GzLERhCQS: Connection refused)
GConf warning: failure listing pairs in `/apps/nautilus/preferences': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-LVk79XkPXU: Connection refused)GConf warning: failure listing pairs in `/desktop/gnome/file_views': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-FQHSOkYllt: Connection refused)GConf warning: failure listing pairs in `/desktop/gnome/background': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-8Xuyk1vdXo: Connection refused)

GConf warning: failure listing pairs in `/apps/nautilus/desktop': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-ozPYTmoETK: Connection refused)^C
dylan@DYLANTAYLOR-PC:~$ sudo bash
root@DYLANTAYLOR-PC:~# nautilus

(nautilus:30540): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-OLvCkpGsUl: Connection refused)
^C
root@DYLANTAYLOR-PC:~# gedit
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-neb7hpKX1m: Connection refused)
^C
root@DYLANTAYLOR-PC:~# firefox
root@DYLANTAYLOR-PC:~# 

```
At first, I thought it was only gedit, so I tried sudo apt-get purge gedit, and then sudo apt-get install gedit ubuntu-desktop. But after it didn't improve, I noticed other commands like nautilus also couldn't be run as root. I have absolutely no idea what's wrong here and I'd appreciate any help.

---

### Post by s.fox on 2009-05-25
Hi,

[This]("http://www.linuxhelp.net/forums/lofiversion/index.php/t8237.html") person on a different forum experienced same error as you.  Maybe the fix they used will work for you aswell.

Hope it does.

-Ash R

---

### Post by ALIENDUDE5300 on 2009-05-25
> **Ash R said:**
> Hi,

[This]("http://www.linuxhelp.net/forums/lofiversion/index.php/t8237.html") person on a different forum experienced same error as you.  Maybe the fix they used will work for you aswell.

Hope it does.

-Ash R

Unfortunately, It didn't... Here's what I tried (in order):
```
root@DYLANTAYLOR-PC:~# chmod 700 /tmp/gconfd-$USER/
chmod: cannot access `/tmp/gconfd-root/': No such file or directory
root@DYLANTAYLOR-PC:~# chmod 700 /tmp/gconfd-dylan/
chmod: cannot access `/tmp/gconfd-dylan/': No such file or directory
root@DYLANTAYLOR-PC:/tmp# ls /tmp
ecryptfs-dylan-Private  Flashgdcbsz            hsperfdata_dylan  keyring-p5kLw0  orbit-root  plugtmp-1  pulse-PKdhtXMmr18n  ssh-BfehN30101        virtual-dylan.OPXxKf
FlashFve6Jl             gedit.root.1697966851  hsperfdata_root   orbit-dylan     plugtmp     plugtmp-2  pulse-XtaXbehvIYw6  virtual-dylan.FTJHl1  virtual-dylan.TjgMT1
root@DYLANTAYLOR-PC:/tmp# chmod 700 /tmp/orbit-dylan/
root@DYLANTAYLOR-PC:/tmp# chmod 700 /tmp/orbit-root/
root@DYLANTAYLOR-PC:/tmp# gedit
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-kDRimwBlKl: Connection refused)
^C
```
No luck at all :(

---

### Post by ALIENDUDE5300 on 2009-05-25
Hmm... I fixed this, but I'm not quite sure how... I simply deleted all the files in ~/.dbus/session-bus, and now it works fine. Can anyone explain how that worked?

---

### Post by BobDoLe on 2009-07-24
> **ALIENDUDE5300 said:**
> Hmm... I fixed this, but I'm not quite sure how... I simply deleted all the files in ~/.dbus/session-bus, and now it works fine. Can anyone explain how that worked?
bah. i got the same issue after an upgrade to 8.10

---

### Post by rlsharpton on 2009-08-03
I had very similar error after installing mysql, apache2, php5, and few other similar items. I used sudo touch /forcefsck && sudo reboot to fix, but was wondering about the touch /forcefsck... how that worked. fsck I understand(mostly) touch I understand, combining the two... not sure what that did.

---

### Post by potatochip on 2009-08-20
> **rlsharpton said:**
> I had very similar error after installing mysql, apache2, php5, and few other similar items. I used sudo touch /forcefsck && sudo reboot to fix, but was wondering about the touch /forcefsck... how that worked. fsck I understand(mostly) touch I understand, combining the two... not sure what that did.


touch creates an empty file, in this case in the root directory and called forcefsck.
when linux boots it does a fsck if the file /forcefsck exists.
So you are simply setting a flag by creating an empty file.

---

### Post by yclian on 2010-04-27
I resolved this issue by deleting ~/.dbus* as suggested by ALIENDUDE5300.

---

### Post by amsterdamharu on 2010-04-27
sudo is not to be used for running gui programs or so I've heard.

Press alt + F2 and type gksu gedit

Maybe running gui stuff in sudo corrupts something although I allays used it before and never had a problem with it. Now I use gksu since it's more continent.

---

### Post by Martje_001 on 2010-04-27
> **ALIENDUDE5300 said:**
> Hmm... I fixed this, but I'm not quite sure how... I simply deleted all the files in ~/.dbus/session-bus, and now it works fine. Can anyone explain how that worked?
Well, DBus is used as a communication-protocol for programs on the system (from low-level to high-level). Maybe a file in .dbus was corrupt and you forced it to create a new connection by removing "lock"- or "state"-files.

---

### Post by jhallward on 2010-05-17
> **ALIENDUDE5300 said:**
> Hmm... I fixed this, but I'm not quite sure how... I simply deleted all the files in ~/.dbus/session-bus, and now it works fine. Can anyone explain how that worked?

Thanks ALIENDUDE5300, this did it for me.

---

