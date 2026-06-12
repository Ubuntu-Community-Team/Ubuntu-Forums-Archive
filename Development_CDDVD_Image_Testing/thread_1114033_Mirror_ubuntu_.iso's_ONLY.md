---
title: "Mirror ubuntu .iso's ONLY"
date: 2009-04-02
forum: Development CD/DVD Image Testing
---

### Post by evilaim on 2009-04-02
Hey everyone, usually I don't post questions, only answers so this should be new...

I'm starting a site up, but the size is hosted on a dedicated server (very high bandwidth).  I need to figure out the best way to auto download any iso's from a mirror (probably MIT) that get released.  So, when a version is released, the dedicated box downloads the iso and then writes the location of that file to a db, then I can have the site auto update with all the new versions.

I've been looking into RSync but I don't know if that will do only the ISO's.  Anyone have any ideas?

Thanks

-Evil

---

### Post by Sam Lars on 2009-04-03
I think rsync would work well, you could point it to only *.iso files.

---

