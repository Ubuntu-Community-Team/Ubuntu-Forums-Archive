---
title: "Zeroconf error in KDE"
date: 2006-06-10
forum: Desktop Environments
---

### Post by PeterB on 2006-06-10
I've installed KUbuntu and updated all packages.  When I go to "Remote Places" and click on *Network Services* (to find a share on another machine) I get the message
"The Zeroconf daemon (mdnsd) is not running"

I have the kdnsd package installed, have added the zeroconf package, and don't know what else to try.  zeroconf binary is in the system path, and there is an empty file at /etc/mdnsd.conf.

How can I get sharing working?  I'm guessing it should be by default, but something appears to be missing.

---

### Post by dunnerz on 2006-07-10
Same problem here

Gnome works fine (which is funny, because this was exactly the other way around before i changed from breezy to dapepr!)

---

### Post by scotty64 on 2006-07-10
My kubuntu zeroconf seems to be moody:
Sometimes it works fine, sometimes I get the "...demon not running..." warning message. Avahi is running and all related packages from universe and multiverse are installed. Any ideas?

---

### Post by dunnerz on 2006-07-10
I'm at home now, so can't try this until tomorrow when I'm at work (the issue is with my work PC, not my home pc - it is becomming quite crucial because I need to access windows shares through Quanta in order to work!!) - anyway I found this link

[http://www.kde-apps.org/content/show.php?content=30424](http://www.kde-apps.org/content/show.php?content=30424)

also found some info about installing avahi ( [http://wiki.kde.org/tiki-index.php?page=Zeroconf+in+KDE](http://wiki.kde.org/tiki-index.php?page=Zeroconf+in+KDE) ), which I will look into too, and will post any out come here.


If anyone else has any suggestions, I'm willing to try those to

Thanks.

---

### Post by dunnerz on 2006-07-11
non of the above worked

i can't access windows shares from KDE


anyone any ideas! PLEASE!!!


](*,) ](*,) ](*,)

---

### Post by dunnerz on 2006-07-11
Right,

now, this is silly of me

if i type WORKGROUPNAME\username in the authentication box, it works

never had to do this before in ubuntu (dont have to do it in gnome), but makes sense!


:rolleyes:

---

### Post by scotty64 on 2006-07-11
> **dunnerz said:**
> Right,

now, this is silly of me

if i type WORKGROUPNAME\username in the authentication box, it works

never had to do this before in ubuntu (dont have to do it in gnome), but makes sense!


:rolleyes:
It looks to me as there is a bug in the authentication box, because I have the same issue with ftp. I have to use an [ftp://username@hostname/blurp](ftp://username@hostname/blurp) URL in order to log in with a particular username. The funny thing is that in this case the authentication box comes up with the username provided in the URL filled in and the whole thing works fine. But when I enter a username in the empty authentication box it just ignores the PASSWORD (according to the ftp-servers error message). ](*,)

---

