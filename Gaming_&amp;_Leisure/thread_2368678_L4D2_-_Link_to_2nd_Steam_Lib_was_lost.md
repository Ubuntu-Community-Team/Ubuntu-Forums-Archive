---
title: "L4D2 - Link to 2nd Steam Lib was lost"
date: 2017-08-13
forum: Gaming &amp; Leisure
---

### Post by javierdl on 2017-08-13
I have a 2nd Steam Library folder in a different HD partition. I had been playing those games without a problem. Until today. For some reason the path to that library is not in the Settings anymore. Normally I just have to remember to be sure to mount that partition before I open Steam, but this time that made no difference. I logged out too and logged back in, without avail though.
I hope there's a way to re-link that library back, because otherwise as you already know, it's a lot of Gbs to re-download.

Thanks guys,

JDL
P.S. Specs:
Acer Predator Desktop 710, i5-6400, 16 Gb ram, Ubuntu 16.04.3 LTS

---

### Post by sccman on 2017-08-13
Try fixing the missing dependencies in Steam:
```
sudo apt update --fix-missing
```

It may create a second Lib, but at least it'll work.

---

### Post by javierdl on 2017-08-14
Thanks for sharing sccman, that's a good one :)
Unfortunately Steam still does not see the 2nd library :(

Maybe if I could add that path to Steam again somehow...
I just renamed my "steamapps" folder to "steamapps_old" and added a new folder and called it "steamapps". 
Then from within Steam I added a new library by pointing at the new "steamapps". 
Then closed Steam, moved all the files and subfolders there to the new folder. There were no hidden files to move.
Steam does show the new path, but is not making use of the files inside :(

Could this work somehow by using either?:
1. Back up and Restore Games...
2. Add a Non-Steam Game to my Library...

I tried the above without success. But I may have been looking in the wrong folders, or just overlooking the correct way.

---

### Post by javierdl on 2017-08-23
What did work was to add that library's folder to the fstab file.

---

