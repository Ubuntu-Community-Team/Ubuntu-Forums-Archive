---
title: "Diskspace disappears"
date: 2009-02-03
forum: General Help
---

### Post by Stolea on 2009-02-03
Something you guys might be able to answer:
My Ubuntu is set up on a200 Gig drive as /boot 1gig, /root 30gig, /swap 20Gig, /home 150gig. I have second 320gig drive for /windows and a third 40 Gig drive for my backups. The 40Gig is permanently mounted as is a windoze partition on another computer.

This configuration has worked flawless until a couple of days ago when VMware said it didn't have enough room for its temp files (/tmp/vmware-peter)
I went and got rid of unnecessary files and freed up 50meg and shifted my backup files from /var/backup to the 40 gig drive. This should have freed up 17Gig, but the partition manager tells me that I still have only 50mb free space on the drive. Vmware certainly still is complaining about the lack of space as are about most applications that have to create temp files.
I have used the disk usage analyzer, but cannot find anything that would account for more than maybe 6gig in total. I stopped the permanent mounted disks from being mounted, thinking that that might have something to do with it. No difference. It would appear that something has made itself at home which is invisible to me.
Any suggestions?

---

### Post by Stolea on 2009-02-03
Addendum:
I Had a bit of a scout around the net and came across an article that among other things suggested to run```
sudo du -h /root
```.
This gave me a list of all the files in root and it would appear that most of my disk space is used up by trash files. 
> 12K	/root/.local/share/Trash/files/google-earth/resources/flightsim/keyboard
12K	/root/.local/share/Trash/files/google-earth/resources/flightsim/hud
8.0K	/root/.local/share/Trash/files/google-earth/resources/flightsim/planet
56K	/root/.local/share/Trash/files/google-earth/resources/flightsim/controller
16K	/root/.local/share/Trash/files/google-earth/resources/flightsim/aircraft
112K	/root/.local/share/Trash/files/google-earth/resources/flightsim
8.0K	/root/.local/share/Trash/files/google-earth/resources/mz.country
8.0K	/root/.local/share/Trash/files/google-earth/resources/ai.country
16K	/root/.local/share/Trash/files/google-earth/resources/en_CA.locale
8.0K	/root/.local/share/Trash/files/google-earth/resources/sk.country
8.0K	/root/.local/share/Trash/files/google-earth/resources/pe.country
5.7M	/root/.local/share/Trash/files/google-earth/resources
59M	/root/.local/share/Trash/files/google-earth
4.0K	/root/.local/share/Trash/files/backdriveexit
32M	/root/.local/share/Trash/files/backup/2009-02-02_07.33.56.690842.Shop.inc
1.7G	/root/.local/share/Trash/files/backup/2009-02-03_07.50.19.540813.Shop.inc
3.1G	/root/.local/share/Trash/files/backup/2009-01-26_10.31.58.714478.Shop.inc
2.9G	/root/.local/share/Trash/files/backup/2009-01-30_08.33.35.317570.Shop.inc
3.0G	/root/.local/share/Trash/files/backup/2009-01-28_08.33.59.699011.Shop.inc
3.1G	/root/.local/share/Trash/files/backup/2009-01-29_08.47.46.838429.Shop.inc
3.0G	/root/.local/share/Trash/files/backup/2009-01-31_10.51.13.965493.Shop.inc
67M	/root/.local/share/Trash/files/backup/2009-02-01_09.20.44.361068.Shop.inc
52M	/root/.local/share/Trash/files/backup/2009-01-27_08.06.15.894665.Shop.inc


How do I get rid of those files?

---

### Post by jerome1232 on 2009-02-03
Delete them, This is what happens when you delete files using "gksu nautilus" alot of people don't realize that root has a trash too, and what your doing is actually moving the files to root's trash. Maybe get in the habit (when running nautilus as root) of shift+deleting which bypasses trash.

```
sudo rm -rf /root/.local/share/Trash/*
```

---

### Post by Stolea on 2009-02-03
Tried it and it didn't delete the files.
Next?

---

### Post by Stolea on 2009-02-03
Shift-delete in sudo nautilus got rid of them.
Thanks a lot
Happy now :)

---

