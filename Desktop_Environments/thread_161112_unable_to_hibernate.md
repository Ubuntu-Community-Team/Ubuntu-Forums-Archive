---
title: "unable to hibernate"
date: 2006-04-16
forum: Desktop Environments
---

### Post by bishwo on 2006-04-16
help,after doing this
to update an existing partitions:
0) open a terminal or enter cli
1) sudo tune2fs -O dir_index /dev/hdXY (where X indicates device, normally a and Y indicates partition, normally 1)
2a) sudo updatedb
alternatively, unmount and do
2b) sudo e2fsck -D /dev/hdXY
from this thread [http://ubuntuforums.org/showthread.php?p=927112#post927112](http://ubuntuforums.org/showthread.php?p=927112#post927112)

I have ended up not being able to hibernate ..
when I hibernate its acts like its going to hibernate ie it turns off the monitor and makes a thud in my speaker and then after a while 
It makes another thud in my speaker and after another while it turns on my monitor and brings the locked so plz login screen..



The thread was really nice though it did speed up my computer

---

