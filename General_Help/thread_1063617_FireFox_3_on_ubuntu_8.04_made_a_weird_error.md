---
title: "FireFox 3 on ubuntu 8.04 made a weird error"
date: 2009-02-08
forum: General Help
---

### Post by heatblazer on 2009-02-08
Just an hour ago, I was browsing with FF3 then a weird error appeared when I tried to download a small file. It said that my download dir is only READ and I don`t have a permission to write there and to select a different one. A seconds after that my aMule closed and refused to open because the ./amule/TEMP is read only then Azureus gave the same error. I opened HOME and right-click to create a new file/folder - it was disabled due to root restricitons... That was weird, I rebooted and a FCSK was performed. At the very begining it stopped giving me an error and required a PASS and a manual usage. I did so. After a confirmed a few "Y"-ses I saw the check disk: there was an error in Mozilla Firefox Cache in ??? fix? [Y] for yes.... Now everything is fine. But that error gave me the creeps....

---

### Post by Yashiro on 2009-02-08
Your filesystem crashed and was re-mounted as Read-Only.

---

### Post by heatblazer on 2009-02-08
No, it`s not that. When I rebooted and first cancelled the FCSK disk, it was all normal. I`ve had full root rights, but when I opened FF3 it happened again. Looks like there was some fishy CACHE, probably... It`s good that I performed it manually... to see the error in CAHCE in ???. What the hell is that ??? in the cache...

---

