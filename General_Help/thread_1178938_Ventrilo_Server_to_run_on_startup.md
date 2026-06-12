---
title: "Ventrilo Server to run on startup"
date: 2009-06-05
forum: General Help
---

### Post by pmcdougl on 2009-06-05
Ok so I am pretty new to linux and I need to know how to run things on startup. I have a webserver up and running now and also want to host a ventrilo server. I have ventrilo server installed and know how to run it, but it doesn't run on startup. To run it I have to change to the directory it is in (/home/username/Applications/ventsrv) and type "./ventrilo_srv" into the terminal. Is there a way to issue this command on start up?

Thanks in advance,
~pmcdougl

---

### Post by pmlxuser on 2009-06-05
easiest way

go to > sysytem > preferences > startup application > ADD
add the 
[code]
/home/username/applications/ventsrv/./ventilo_srv  
[code]
or comething close to that
or you can just browse to the folder till you find the binary ventilo_srv

after that save changes and next time you log in viola

---

### Post by pmlxuser on 2009-06-05
easiest way

go to > sysytem > preferences > startup application > ADD
add the 
[code]
/home/username/applications/ventsrv/./ventilo_srv  
[code]
or comething close to that
or you can just browse to the folder till you find the binary ventilo_srv

after that save changes and next time you log in viola

---

### Post by pmcdougl on 2009-06-05
I tried that before and now have tried it again, it didn't start ./ventrilo_srv on start up. I don't know if it is because those kind of commands cannot be issued in the start-up programs or if it needs to be run as an administrator (sudo su)...I was also thinking that I could make it a command straight from terminal (i.e. "gedit" or "firefox") and just make a shortcut on the desktop. But I don't know how to do that.

The reason I need everything to run on start-up is that I want it to be as easy as possible for a laymen to turn on my server and have all of its services work.

---

