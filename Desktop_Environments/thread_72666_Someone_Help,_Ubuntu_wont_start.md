---
title: "Someone Help, Ubuntu wont start"
date: 2005-10-07
forum: Desktop Environments
---

### Post by zac851 on 2005-10-07
I was following the directions to installing the Nvidia drivers here ([http://www.ubuntuforums.org/showthread.php?t=573680](http://www.ubuntuforums.org/showthread.php?t=573680).  I got to the part where I had to press CTRL+ALT+F1 and realized I forgot what directory I saved the driver in.  I figured no big deal and I would just start kdm back up.  I typed sudo /etc/init.d/kdm start and the screen flashed  and it said  Starting KDM diplay or something along those lines       [OK]      but then went to the command like username@xxxx# or whatever it is.    Now I cant get back on.  I also tried sudo /etc/init.d/gdm start but it said it wouldnt start that either since it wasnt my default display manager.  What do I do?!?!

---

### Post by aysiu on 2005-10-07
What happens when you try to type in ```
startx
``` ?

---

### Post by zac851 on 2005-10-07
Please forgive the errors I typed this quickly frmo looking at the screen  

(EE) FILED TO LOAD MODULE "NVIDIA" (MODULE does not exist, 0)
(EE) No Drivers available.

Fatal server Error 
no screens found

please consult the The X.org foundation support at xxx.xxxx.xx

Please also check the log file at /var/log/xorg.0.log for addiotnal info

X10: fatal I0 error 104 (connection reset by peer) on x server ":0.0"
after 0 request 90 known processed) with 0 events remaining

---

### Post by codejunkie on 2005-10-07
[QUOTE=zac851]Please forgive the errors I typed this quickly frmo looking at the screen  

(EE) FILED TO LOAD MODULE "NVIDIA" (MODULE does not exist, 0)
(EE) No Drivers available.

Fatal server Error 
no screens found

please consult the The X.org foundation support at xxx.xxxx.xx

Please also check the log file at /var/log/xorg.0.log for addiotnal info

X10: fatal I0 error 104 (connection reset by peer) on x server ":0.0"
after 0 request 90 known processed) with 0 events remaining[/QUOTE]
try this ```
sudo init 1
``` wait till it shuts down all the services and then 
```
sudo init 5
``` this happens when you are trying to start x when it is already running.

---

### Post by zac851 on 2005-10-07
at first I ran both those commands then ran the kdm start command and it still didnt start.  so I ran the commands you gave me again to kill everything then ran startx and got pretty much the same error I really hope I don't have to reinstall again. :(

> skipping  usr/x11r6/lib/modules/extentions/libglore.a:m_debug_clip.o": no symblos found 
skipping  usr/x11r6/lib/modules/extentions/libglore.a:m_debug_clip.o": no symblos found 
skipping  usr/x11r6/lib/modules/extentions/libglore.a:m_debug_clip.o": no symblos found 


(EE) FILED TO LOAD MODULE "NVIDIA" (MODULE does not exist, 0)
(EE) No Drivers available.

Fatal server Error 
no screens found

please consult the The X.org foundation support at xxx.xxxx.xx

Please also check the log file at /var/log/xorg.0.log for addiotnal info

X10: fatal I0 error 104 (connection reset by peer) on x server ":0.0"
after 0 request 90 known processed) with 0 events remaining

xauth: error in locking authority file /home/zac851/.Xauthority

---

### Post by codejunkie on 2005-10-07
[QUOTE=zac851]at first I ran both those commands then ran the kdm start command and it still didnt start.  so I ran the commands you gave me again to kill everything then ran startx and got pretty much the same error I really hope I don't have to reinstall again. :([/QUOTE]
you could try this 
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
if your display was configured correctly during the install this will reconfigure the xserver and set it to default settings, this should get the gui up and running then you can reinstall the nvidia driver.

---

