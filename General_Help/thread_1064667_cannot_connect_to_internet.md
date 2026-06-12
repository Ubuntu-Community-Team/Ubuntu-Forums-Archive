---
title: "cannot connect to internet"
date: 2009-02-09
forum: General Help
---

### Post by civillian on 2009-02-09
When I have my computer connected to the wired connection in my university's halls of residence (connecting using an 802.1x secure connection with EAP-PEAP, MSCHAPV2) the connection will work for a while after connecting following login, however, every now and then the connection will stop working.
I checked with the sysadmin, and he said that

> 
looking at the logs it looks like your computer has not been
authenticating every time, you should check it is sending the correct login
credentials so it can re-authenticate every time it is challenged.

I have all the network logins and passwords set up for the connection, so in theory it should just resend, however, it apparently doesn't, which means I have to manually reconnect (re-select the network and wait for authentication) which while not serious, can be annoying when I'm using pidgin or watching iPlayer etc.

Any help is welcome, and it should be noted that I cannot get packages from apt-get as the ports it uses are blocked by the network admins so any packages I want to install i have to download from packages.ubuntu.

Thanks for any help.

---

### Post by TeoBigusGeekus on 2009-02-09
Grab your flash drive, go to a friend of yours download wicd
[http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=659059]("http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=659059")
and install it.
It is much better than gnome network manager. After that...:???:

---

### Post by civillian on 2009-02-09
using it now, hopefully it will keep me connected! (but it seemed to auto connect to the network with no issues, and hasn't required any setup so far!)

---

### Post by civillian on 2009-02-09
update: it connected at first, not sure how since it didn't need any config...

how would I configure wicd to connect to a secure wired 802.1x network, using peap and needing a private id and a username and password?

what config files should I edit, where should it go! I checked the man page for wicd and it wasn't really very enlightening...

---

### Post by TeoBigusGeekus on 2009-02-10
> **C!V!NT said:**
> update: it connected at first, not sure how since it didn't need any config...

Wicd replaces gnome network manager taking all settings from there.

If you go to Applications->Internet->Wicd I'm sure you'll find something to fiddle with...

---

### Post by civillian on 2009-02-10
it didnt seem to, and if it did then it didn't work very well, it seemed to be fairly vanilla, and requiring lots of config file editing/creating.
It looked great for wireless, however...just for the wired it seemed...lacking, it had no config options to speak of for secure wired connections (which is what I needed since I'm connected through a proxy server hosted by my university) unless I wanted to fiddle about with config files which were not very well documented for newbs :(
I might try it on my eeePC though (after I've installed pupeee instead of eeebuntu (which is reeeeally slow))
But on my desktop I'll stick with what I know for now, and try to find some kind of setting which will fix my problem in network manager, since it seems a lot easier to configure (to me).

---

### Post by imdano on 2009-02-11
Wicd doesn't actually support wired encryption yet, which is likely why you found it difficult to configure.  You could probably come up with a way to do the authentication by manually running wpa_supplicant through wicd's scripts feature, though.

---

### Post by civillian on 2009-02-12
that seems like a good project, but tbh I don't have the time at the moment to try stuff like that, so unfortunately for now I'm still running network manager.

Thanks for the help anyway guys :)

---

