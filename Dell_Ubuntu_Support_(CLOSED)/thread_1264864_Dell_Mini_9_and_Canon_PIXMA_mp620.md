---
title: "Dell Mini 9 and Canon PIXMA mp620"
date: 2009-09-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by merdock69 on 2009-09-12
I've tried desperately for 3 days to get this stupid printer installed and i just can't get it. Can someone offer up some assistance. I've tried the links listed below 

[http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html](http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html)

[http://www.nervous.it/2009/04/canon-pixma-mp620-wireless-on-ubuntu/](http://www.nervous.it/2009/04/canon-pixma-mp620-wireless-on-ubuntu/)

[http://ubuntuforums.org/showthread.php?t=1016130](http://ubuntuforums.org/showthread.php?t=1016130)

[http://ubuntuforums.org/showthread.php?t=1048629](http://ubuntuforums.org/showthread.php?t=1048629)

I basically get stuck after installing cnifilter-common3.00. After this successfully installs I get an error trying to install the cnijfilter-mp610series_2.80-1_i386.deb, It comes back with an error message "cnijfilter-common" deoendency can not be satisfied...

I don't get it it... I've followed all the instructions in the threads above and no dice.

---

### Post by merdock69 on 2009-09-13
UPDATE, problem resolved

---

### Post by merdock69 on 2009-09-15
Had to simply copy sidechannel.h to the correct folder. Got it out of a package download and just copied it using sudo. That solved my problem.

---

