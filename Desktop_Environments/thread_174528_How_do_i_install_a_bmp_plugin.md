---
title: "How do i install a bmp plugin"
date: 2006-05-12
forum: Desktop Environments
---

### Post by dhruv_1884 on 2006-05-12
hi, i downloaded the gz file of the m4a bmp plugin.
it has the files libmp4.so and libmp4.la in it.
i dont know how ti install these files

could somebody please give me the procedure

thanks

regrds 
-
dc

---

### Post by johnc4510 on 2006-05-12
Try this site:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by dhruv_1884 on 2006-05-12
Dude i tried 
./configure
make
sudo make install

nothinghappened,
attached the screen shot

regards
-
dc

---

### Post by dhruv_1884 on 2006-05-12
dudes please any help!!!!!!!!!!!!!

i need the to install the mp4 plugin on bmp


could some one plz tell me what i could do


thanks

regards
-
dc

---

### Post by depu on 2006-05-12
i think u need to install checkinstall before u can run ./configure and make install
sudo apt-get install checkinstall
its there in the repos

---

### Post by y0ssarian on 2006-05-31
I'm running dapper with the universe and multiverse enabled and 'sudo apt-get install bmp-mp4' worked for me

---

