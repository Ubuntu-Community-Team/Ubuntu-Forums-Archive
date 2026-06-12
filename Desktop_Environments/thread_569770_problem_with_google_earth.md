---
title: "problem with google earth"
date: 2007-10-07
forum: Desktop Environments
---

### Post by tropcky on 2007-10-07
hi 
i trayed to install Google earth  so many times but i got the same err msg  

tropcky@tropcky-Linux:~$ wget [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
--19:23:47--  [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 209.85.135.91
Connecting to dl.google.com|209.85.135.91|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:23:49 ERROR 404: Not Found.

tropcky@tropcky-Linux:~$ 


any help  ?
thank u

---

### Post by ares1983 on 2007-10-07
That is not a valid url for the .bin, I think they have changed the download location use 

[http://dl.google.com/earth/client/current/GoogleEarthLinux.bin]("http://dl.google.com/earth/client/current/GoogleEarthLinux.bin")

hope that helps

---

### Post by tropcky on 2007-10-07
thank u for heloing but its the same problem

---

### Post by ares1983 on 2007-10-07
are you sure? make sure you are using the hyperlink i posted not the text I get this:

[I]alex@ares:~$ wget [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)
--21:18:47--  [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)
           => `GoogleEarthLinux.bin'
Resolving dl.google.com... 66.249.93.91
Connecting to dl.google.com|66.249.93.91|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 23,042,785 (22M) [application/octet-stream]

100%[====================================>] 23,042,785   841.99K/s    ETA 00:00

21:19:11 (937.08 KB/s) - `GoogleEarthLinux.bin' saved [23042785/23042785]

alex@ares:~$ [/I]

---

### Post by Gremlinzzz on 2007-10-07
googleearth is in synaptic package manager install from there.

---

