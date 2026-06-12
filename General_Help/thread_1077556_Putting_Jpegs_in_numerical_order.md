---
title: "Putting Jpegs in numerical order"
date: 2009-02-22
forum: General Help
---

### Post by Doug11 on 2009-02-22
Hi,,I was just trying to sort out all my pictures. Was just wondering if there was a way to have them all named in numerical order. Some of them were taken with different cameras and are all named different with different alpha numerical sequences. And some are different pics but with the same title. Thought there might be a way to highlight them all and then rename some how. Any help would be appreciated.

---

### Post by yeleek on 2009-02-23
Google is your friend :)

[http://ubuntuforums.org/archive/index.php/t-79547.html](http://ubuntuforums.org/archive/index.php/t-79547.html)

i.e.

egon spengler
October 21st, 2005, 12:58 AM
Another alternative is for i in *.jpg ; do mv $i newname$((++n)).jpg; done


This will rename every jpg in the diretory newname1.jpg, newname2.jpg -> newname100.jpg

---

