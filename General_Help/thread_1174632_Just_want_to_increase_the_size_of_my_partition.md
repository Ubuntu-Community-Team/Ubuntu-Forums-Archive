---
title: "Just want to increase the size of my partition"
date: 2009-05-31
forum: General Help
---

### Post by kmaster228 on 2009-05-31
hello all i recently instaled ubuntu on a 15 gb partiton dual botting with vista... i have realised that 15 gb isnt enough for my needs... i simply want to increase my partition size without losing any data or making a new partion.. i have gparted installed. i have included a snap shot of what gparted looks like in my case [ATTACH]115856[/ATTACH]

---

### Post by dandnsmith on 2009-05-31
Not the best idea to post the same problem twice ([see this posting](http://ubuntuforums.org/showthread.php?t=1174638))

---

### Post by Minsky on 2009-05-31
I think you need to do the re-partitioning from a live CD as you cannot modify a partition whlst it is mounted. The way I would do it, is to create an image of your Ubuntu partition (using a program such as Clonezilla for example), then boot from a live CD and resize the partiton, and restore the image into the modified partition afterwards. You can also follow step by step instructions here - [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

