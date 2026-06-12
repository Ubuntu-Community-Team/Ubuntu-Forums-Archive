---
title: "right click &gt;&gt; &quot;send to ...&quot; menu doesn't appear"
date: 2011-07-22
forum: Desktop Environments
---

### Post by kovo1533 on 2011-07-22
Hello I have a problem when I browse folders and want something to send to my nokia 6300 over bluetooth. In past I just right click and choose "send to..." >> "bluetooth" and choose device from list. Few weeks ago it stopped working - i click "send to" and nothing will happen ... menu will not show ... have anyone the same problem or can help me please ? :D My ubuntu version is 10.04 (lucid)

---

### Post by Enigmapond on 2011-07-22
If you install ubuntu-tweak, it has a function to control the nautilus scripts. Either that or just download this [http://gnome-look.org/content/show.php/Send+to...?content=67627](http://gnome-look.org/content/show.php/Send+to...?content=67627) and put it in home/gnome2/nautilus scripts.

Cheers!

PS make sure you make it execute chmod -x

---

### Post by kovo1533 on 2011-07-22
Thanx this works but it is only the halfway solution ... now at first I must have my nokia mounted (must show as remowable device ni nautilus side panel) ... the original solution in ubuntu showed menu with destinations where i choosed bluetooth and then list with mobile devices that computer remembers from past or search bluetooth devices ... the pretty thing on this solution was that if my nokia wasn't mounted it mounts the phone and continue to file transfer ... it was fast and energy saving

---

### Post by kovo1533 on 2011-07-22
OK after few hours I find out what was wrong. I had libnautilus-extension1 and libnautilus-extension1-dev librarires different version as nautilus-sendto due tunning i made to nautilus (installing nautilus-elementary from PPA). thank for all who wanted to help and it's time to mark thread as solved.

if you have exact problem i resolve it by temporalily adding repositories for newer version of ubuntu into my repositories, from synaptic upgraded mentioned packages to newer and equal version and then remove added repositories and restart nautilus by running:
```
killall nautilus
```

---

