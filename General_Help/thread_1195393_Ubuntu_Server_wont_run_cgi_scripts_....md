---
title: "Ubuntu Server wont run cgi scripts ..."
date: 2009-06-23
forum: General Help
---

### Post by wwsoft on 2009-06-23
Hello , I am running ubuntu server i386 - 32bit , I have php5 , apache2  etc installed but my cgi scripts when I try to access them  from another computer it dosent run the script I am hoping to get some help if its configuration , lack of hardware I hope someone can point me in the right direction. :)

---

### Post by blueridgedog on 2009-06-23
When I am debugging apache CGI scripts, I generally keep a terminal up on the server and after getting an error, tail the error log of apache.  Usually that gets the debugging process started by pointing to a bad script, bad permissions or bad configuration of apache.

---

### Post by wwsoft on 2009-06-28
> **blueridgedog said:**
> When I am debugging apache CGI scripts, I generally keep a terminal up on the server and after getting an error, tail the error log of apache.  Usually that gets the debugging process started by pointing to a bad script, bad permissions or bad configuration of apache.
  thanks for the advice ! I fixed it too

---

