---
title: "dell d600 - ipw2100 wifi error"
date: 2007-12-07
forum: Dell  Ubuntu Support
---

### Post by puccaso on 2007-12-07
there is something up with the wifi on the dell. i dont know why. it used to work - and i just stopped. 
it keeps saying it times out whilst associating. why is this?

wwhat info can i give you to help me fix this

---

### Post by erichill on 2007-12-08
I have been having similar problems with my Inspiron 1501.
To cut a long story short, I have added the IP address of my router to the /etc/avahi/hosts file e.g. 192.168.1.1 router.local

This seems to be working and I am reporting on it periodically in alt.os.linux.ubuntu

You might get the same effect by adding your router address to the hosts list in your network connection, but I have not tried that yet.

Hope this helps

Eric :)

---

