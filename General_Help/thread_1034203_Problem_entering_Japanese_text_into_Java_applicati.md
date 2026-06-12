---
title: "Problem entering Japanese text into Java applications"
date: 2009-01-08
forum: General Help
---

### Post by ForumUser1234567890 on 2009-01-08
I have 8.10, with Anthy and SCIM installed.
I cannot use the Japanese input method (Anthy) on any Java application.
I can copy and paste Japanese text into a Java application, and the appropriate fonts are installed, but I just can't type it in.
I've searched for solutions and nothing has worked so
I'm wondering if it is related to another problem I have.
It's a complete guess because I really don't know.
Quite a few files in my home folder have screwed up permissions.
E.g. doing the following 

ls -lah -R | grep '\?' 

I get
ls: cannot access .recently-used.xbel: Stale NFS file handle
ls: cannot access .viking: Stale NFS file handle
ls: cannot access .viking-maps: Stale NFS file handle
-?????????   ? ?    ?       ?                ? .recently-used.xbel
d?????????   ? ?    ?       ?                ? .viking
d?????????   ? ?    ?       ?                ? .viking-maps
ls: cannot access ./.config/gtk-2.0/gtkfilechooser.ini: Stale NFS file handle
-?????????  ? ?    ?       ?                ? gtkfilechooser.ini
ls: cannot open directory ./Documents/xshogi_src/gnushogi-1.3.2: Permission denied
ls: cannot access ./.gconf/system/networking/connections/10/802-11-wireless-security/%gconf.xml: Stale NFS file handle
-????????? ? ?    ?       ?                ? %gconf.xml
ls: cannot access ./.gconf/system/networking/connections/10/connection/%gconf.xml: Stale NFS file handle
-????????? ? ?    ?       ?                ? %gconf.xml
-????????? ? ?    ?       ?                ? %gconf.xml
ls: cannot access ./.gnome2/gnome-power-manager/profile-48840-charging.csv: Stale NFS file handle

The list goes on.
Now I've seen some posts about restarting the nfs.client, but it seems that isn't on Ubuntu? Or maybe it's called something else.
Also I've tried umount, but I can't umount the /home partition as it seems ubuntu always needs to keep some files open. (Or I guess that's the reason).
Even going to a failsafe terminal and doing a lsof,
you always have the bash process running in /home/mark

Anyway, I've had quite a lot of inexplicable problems such as getting my wireless card to auto-connect, and getting it to hibernate properly. So I feel like these Stale NFS file handles may be related to at least those problems and probably a few others where the config files are screwed up.

Anyone got any ideas how I can delete/fix these files.
Or any other ideas about why the Japanese text in Java isn't working?

---

### Post by AlnCool on 2009-04-28
Hi there !
I have installed Ubuntu 9.04 and i have the same problem. I can't use SCIM-Anthy in java webpage. 
Openoffice is ok, i can type in but as for the following website that is full java, i can't write anything... just read japanese characters : [www.sharedtalk.com](www.sharedtalk.com)

Can someone take a look at it ? Please.

AlnCool

---

### Post by sirgazil on 2009-06-16
> **AlnCool said:**
> Hi there !
I have installed Ubuntu 9.04 and i have the same problem. I can't use SCIM-Anthy in java webpage. 
Openoffice is ok, i can type in but as for the following website that is full java, i can't write anything... just read japanese characters : [www.sharedtalk.com](www.sharedtalk.com)

Can someone take a look at it ? Please.

AlnCool

AlnCool, that Web site is made with Flash not Java.

Anyway, I'd like to know too how to write in Japanese in Java programs. I know there are some things called bridges to be able to use scim in different GUI Toolkits (scim-bridge-client-gtk, scim-bridge-client-qt), but I can't find something similar for Java swing.

---

### Post by AlnCool on 2009-06-17
Hi sirgazil,

You're true, it's a website made with flash 10 now ... but i still have the problem and no one is able to help ... Still no solution on my side :(

---

