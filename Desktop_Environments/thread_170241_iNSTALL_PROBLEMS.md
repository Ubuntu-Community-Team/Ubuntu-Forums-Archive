---
title: "iNSTALL PROBLEMS"
date: 2006-05-04
forum: Desktop Environments
---

### Post by dhruv_1884 on 2006-05-04
hi,
i am trying to install a driver for my webcam
got the * .tar.gz from the net
extracterd it
ran 
./configure

error message
no such file found


then ran make
got the following error


root@dhruv:/home/dhruv/spca5xx-20060501# make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/dhruv/spca5xx-20060501 CC=cc modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
root@dhruv:/home/dhruv/spca5xx-20060501#



any idea wht i should do............

regards

dc

---

### Post by Sef on 2006-05-04
Did you change to the directory where the you extracted to?

---

### Post by dhruv_1884 on 2006-05-04
i changed the directory to the extracted one and then ran the commands from there.
its all in the screen shot

thanks

regards
-
dc

---

### Post by louis_nichols on 2006-05-04
I think [this thread]("http://ubuntuforums.org/showthread.php?t=75284") might help you too

---

### Post by dhruv_1884 on 2006-05-05
thanks dude it worked

---

