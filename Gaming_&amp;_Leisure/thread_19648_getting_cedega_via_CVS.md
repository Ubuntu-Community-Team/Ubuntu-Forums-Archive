---
title: "getting cedega via CVS"
date: 2005-03-12
forum: Gaming &amp; Leisure
---

### Post by Ryan450 on 2005-03-12
I seen somewhere online that you can get cedega for free if you get the sources from CVS? I checked thier website and I cant seem to find that info.. is this offer/chance no longer avaliable? anybody know the command to get it?

---

### Post by RastaMahata on 2005-03-13
[QUOTE=Ryan450]I seen somewhere online that you can get cedega for free if you get the sources from CVS? I checked thier website and I cant seem to find that info.. is this offer/chance no longer avaliable? anybody know the command to get it?[/QUOTE]
 [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

---

### Post by Ryan450 on 2005-03-13
You are running as root.  Do you want a local config file,
file, ~/.wine/config, created?
(yes/no) yes
Searching for an existing Windows installation... not found. (no matching /etc/fstab mount entry found)

Windows was not found on your system, so I assume you want
a Wine-only installation. Am I correct?
(yes/no) no

Aborting install. Make sure your Windows partition is mounted and try again,
or create /root/.wine/config manually by copying from documentation/samples/config and adapting the drive paths.
root@Fletchbox:/home/ryan450/winex #



ok, this is what I got at the end of my winex install, wasnt sure what the local config file would do for me.. could someone please explain the advantages/disadvantages to it? and also how to mount the windows partition? that would be very usefull :)

---

### Post by Ryan450 on 2005-03-13
well I got my windows partition set up to be auto-mounted at boot up now :).. 

but this is driving me crazy!

Searching for an existing Windows installation... not found. (no matching /etc/fstab mount entry found)

Windows was not found on your system, so I assume you want
a Wine-only installation. Am I correct?
(yes/no) no

Aborting install. Make sure your Windows partition is mounted and try again,
or create /root/.wine/config manually by copying from documentation/samples/config and adapting the drive paths.

thats near the end of my winex install.. my windows partition is mounted. any ideas on a fix?

---

### Post by florizs on 2005-04-01
show us your /etc/fstab file.
maybe it willl help

---

