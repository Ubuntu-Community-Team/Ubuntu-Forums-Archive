---
title: "Tango GPS, connecting bluetooth reciever with Gpsd?"
date: 2009-03-30
forum: General Help
---

### Post by savantelite on 2009-03-30
Under Jaunty I have finally synced up my Holux M1200 GPS reciever dongle via bluetooth to my Asus EEE 1000HE. 

Under configurations it lists an IP address for GPSD??? Here is where I am stuck what is my bluetooth dongle IP Address. Where do I find it. is it the same for every thing?

Thanks for any help

---

### Post by savantelite on 2009-03-30
The listener port is under 2947 but what should my IP be set at?

[http://gpsd.berlios.de/#documentation](http://gpsd.berlios.de/#documentation)

---

### Post by savantelite on 2009-10-09
bluetooth is easier than ever under karmic but I am still having issues reading the coordinates of the dongle. I think that I am missing the right ip for gpsd.

---

### Post by a_petrov303 on 2010-05-28
the same problem here:

I do get the coordinates from the gps (on board in my case - Ericsson WWAN/GPS card which came with Lenovo X200) but do not know what is the right IP for gpsd

see the screenshot attached

[http://img576.imageshack.us/img576/6172/screenshot2lf.png](http://img576.imageshack.us/img576/6172/screenshot2lf.png)

---

### Post by a_petrov303 on 2010-05-28
also will be checking this page [http://www.tjansson.dk/?p=450&cpage=1#comment-32373](http://www.tjansson.dk/?p=450&cpage=1#comment-32373) to see if any help comes out of it

---

### Post by ckgreenman on 2010-06-08
If you're trying to connect to a gpsd running on your local system then use 127.0.0.1.

---

