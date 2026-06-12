---
title: "Kubunto 8.10 slows down w/ constant hdd access"
date: 2009-04-03
forum: General Help
---

### Post by enigmatic28 on 2009-04-03
Hi all,

My installation of Kubuntu 8.10 is becoming very slow and shows constant hdd access since the hdd light is always lit even after a cold boot.

the onlything that i have done recently was the following:
1. installed kde 4.2
2. after installation and restarted the system, it showed that new updates were found so i upgraded.

then after restarting, the system shows continuous hdd access..

i have just come from a fresh install so the hdd still have lots of space.

the laptop that i use is has the following specifications:
1.87Ghz CoreDuo
2 Gig ram
ATI x200m video w/ 128 shared
80gig ide

i'm sure that my system can handle the default eye candy that was set in KDE 4.2 since i already tried the latest Beta of Kubuntu 9.04

i'm also not sure if there is an indexing of hdd being done by the system.

thanks..

---

### Post by kevstar31 on 2009-04-03
Open up a termainal and type **cat /etc/fstab** and post the output.

---

### Post by enigmatic28 on 2009-04-03
Hi,

here is the results:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a4666618-e346-4ba0-9647-5ff219b69e4e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d3d95ef1-2df3-4d94-b3e2-da71735e5863 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by kevstar31 on 2009-04-03
At what point does the continuous hdd access start happening?

---

### Post by enigmatic28 on 2009-04-04
during start-up, when the system start to load services.

another thing that bothers me beside the continuous hdd access is that when i brows the internet using Firefox is that it loads the pages very very long even if i have a decent connection and i'm not downloading files, sometimes i will need to constantly hit the refresh button..

i also checked the cpu usage, and the cpu utilization is playing about 40-55% with firefox and uTorrent loaded. though i'm not sure how accurate built-in monitoring tool of KDE, but it show that the highest utilization was from Xorg, but it is just on 12% and on the terminal using top command, it shows that Xorg uses about 12-22% other than that, no process is being shown with high cpu utilization..

thanks...

---

### Post by enigmatic28 on 2009-04-05
help.. any one.....

---

### Post by enigmatic28 on 2009-04-06
i'm getting a bit concerned on the continuous hdd access so i reformated my laptop. and now it is back to normal

---

