---
title: "Need libstdc++6  version 4.0.2 - how do I get it?"
date: 2006-01-10
forum: General Help
---

### Post by Roobert on 2006-01-10
I'm trying to upgrade my gdal-bin and libgdal1c2 packages so that I can run Grass GIS. Synaptic complains that I can't upgrade these packages until I first upgrade my libstdc++6 from version greater than or equal to 4.0.2, but that this version is unavailable. I found the Debian page for libstdc++6 at 
[http://packages.debian.org/unstable/libs/libstdc++6]("http://packages.debian.org/unstable/libs/libstdc++6")


Is this the correct site to download this package from, and how do I get this site into Synaptic?

Thanks!

---

### Post by lamego on 2006-01-10
My advice is to not mix debian packages on ubuntu, specially one like this which may conflict with the existing libs.
Try to get a package of the application for ubuntu or compile it from the source...

---

### Post by Roobert on 2006-01-10
Thanks. Does anyone know where I might be able to download the source for this library? The Debian site seems to be down right now.

---

