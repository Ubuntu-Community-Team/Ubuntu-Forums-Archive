---
title: "How to use cp to traverse a directory looking for sub-directories of a certain name?"
date: 2009-01-11
forum: General Help
---

### Post by Ted_Smith on 2009-01-11
Hi

I have a directory called 'Photography' that holds sub-directories containing photos for each shoot. Beneath each shoot folder is a folder called 'BestShots' that holds JPG exports of my best shots from each shoot. 

I want to traverse the entire 'Photography' folder to find all the JPG files within folders called 'BestShots'. 

For example, 

/mnt/RAID/Photography/2008/08_01_30_Shoot1/BestShots/bestphoto1.JPG
/mnt/RAID/Photography/2008/08_02_15_Shoot2/BestShots/bestphoto2.JPG
/mnt/RAID/Photography/2008/08_03_26_Shoot3/BestShots/bestphoto3.JPG

(the numer45ical naming is just for ease of clarity. The names vary considerably so I just want it to search for the JPG files generally)

I have tried : 

 ls -R /mnt/RAID/Photography/2008/*/Best*/*.jpg

but that is only retrieving about two dozen jpg files. There are hundreds more that, for some reason, are not being listed? 

Ted

---

### Post by heindsight on 2009-01-11
try using the find command instead
for example
```
find /mnt/RAID/Photography -wholename "*/BestShots/*.JPG
```

---

