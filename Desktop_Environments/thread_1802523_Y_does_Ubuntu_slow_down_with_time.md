---
title: "Y does Ubuntu slow down with time"
date: 2011-07-12
forum: Desktop Environments
---

### Post by reptilezone2002 on 2011-07-12
i put ubuntu 11.04 when the day it released ( clean install) it was supper fast when i installed but now its getting slower & slower the boot time is much slower than before no additional software was installed  & the os is the same when i installed it well it happend to the earler versions to 

any ideas why this is happening i thought only windows gets slower with the time

---

### Post by ~!geek!~ on 2011-07-12
It is common to notice this in ubuntu (from my experience). 
I believe this is because of a lot of services and applications set to start at boot time with time (unreadahead helps a lot but still system boots slower). Similarly shutdown time also increases (not to the extent it is for boot time.) It is because of the increased no. of services and applications to be stopped before shutting down. Different servers like apache, mysqlserver, dictserver are common which are started at boot time and shuts down when you shut the system down.  

You may google for terms init.d scripts, unreadhead, services at boot time etc. if it annoys you much. I hope this is what u were talkin about!!!

---

### Post by Bucky Ball on 2011-07-12
... you could also go to 'Sessions and Startup' and disable what you don't use so those services don't start at boot.

---

### Post by reptilezone2002 on 2011-07-12
yes i already disabled the startup items already .. its not annoying but its the same as windows heheh but not that worse .. i thought there is a way around this 


tx for ur comments

---

