---
title: "Yafray 0.8 and Blender 2.3.7"
date: 2005-07-21
forum: Deferred/Invalid Requests
---

### Post by DarkT on 2005-07-21
Having these two packages would be great. Blender is needed less as it will run from a directory in home fine but yafray goes a bit loopy every time I try to build it myself  :-? 
Depending on which yafray source you build you may need to update the OpenEXR lib aswell.
 
Thanks:)

---

### Post by jdong on 2005-07-21
Both not in Breezy

---

### Post by secundar on 2005-08-04
Yafray 0.8 needed a more recent libc6 than ubuntu could provide. I was looking thru some other threads and found this repository to provide the newer libc6...

deb [http://ftp.cl.debian.org/debian/](http://ftp.cl.debian.org/debian/) sarge main non-free contrib

But be careful, it could break other things also. Once libc6 and yafray are installed and working i intend to uncheck this repository in synaptic to be safe.

---

