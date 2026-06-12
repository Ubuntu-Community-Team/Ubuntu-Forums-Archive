---
title: "updates not installable"
date: 2008-12-03
forum: General Help
---

### Post by philetus on 2008-12-03
I show a bunch of updates in update manager, but I can't enable the check boxes.
I need a clue.

---

### Post by Titan8990 on 2008-12-03
They should be checked by default. Try upgrading from the terminal:


sudo apt-get upgrade

---

### Post by philetus on 2008-12-03
I did that and it said "the following updates have been kept back".

They were alsa and pulseaudio updates.

---

### Post by Titan8990 on 2008-12-03
That is because they required additional dependencies. This command will upgrade those that need extra stuff:


sudo apt-get dist-upgrade

---

### Post by philetus on 2008-12-03
~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  alsa-utils libpulsecore5 pulseaudio pulseaudio-esound-compat
  pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11
  pulseaudio-module-zeroconf
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

---

### Post by Titan8990 on 2008-12-03
Try this one:


sudo aptitude full-upgrade



Although that command is supposed to be the same as dist-upgrade....

---

### Post by philetus on 2008-12-03
They appear to be Hardy packages, which would be a downgrade.

Keep the following packages at their current version:
libpulsecore5 [0.9.10-1ubuntu1 (hardy, now)]
pulseaudio [0.9.10-1ubuntu1 (hardy, now)]
pulseaudio-esound-compat [0.9.10-1ubuntu1 (hardy, now)]
pulseaudio-module-gconf [0.9.10-1ubuntu1 (hardy, now)]
pulseaudio-module-hal [0.9.10-1ubuntu1 (hardy, now)]
pulseaudio-module-x11 [0.9.10-1ubuntu1 (hardy, now)]
pulseaudio-module-zeroconf [0.9.10-1ubuntu1 (hardy, now)]

---

### Post by Titan8990 on 2008-12-03
Thats odd. You might want to consider bug reporting that.

---

### Post by philetus on 2008-12-03
In my software sources, under the updates tab, "Ubuntu Updates", all four say Hardy.Is that normal for Intrepid?

---

### Post by Titan8990 on 2008-12-03
I wouldn't think so but I don't have a Intrepid machine to check on. Hopefully someone else will drop in and give some insight.

---

### Post by philetus on 2008-12-03
I fixed my sources list and everything is good.

---

### Post by Titan8990 on 2008-12-03
Was thinking about what might have happened. When you upgrade you get the option to replace or keep your sources.list. You probably opted to keep the old ones.

---

