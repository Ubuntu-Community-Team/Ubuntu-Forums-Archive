---
title: "Synaptic problem"
date: 2005-10-20
forum: Desktop Environments
---

### Post by aham925925 on 2005-10-20
Hey

I ran this debian file which i think downloads w32codecs

I exit and not i cant use synaptic or "apt-get".  Along with not using it...i get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Any Idea how to fix this???

Its to install codecs to watch movie trailers.  Seperate problem to my other post for the movie trailers :( 


Please reply 
cya

---

### Post by Ampersand on 2005-10-20
Try running 
```
sudo dpkg --configure -a
```
If that doesn't work, post the error message here.

---

### Post by aham925925 on 2005-10-20
It tries to connect to the package.

This doesn't work as the connection times out.

Any thoughts?

---

### Post by Zotova on 2005-10-20
I had the same problem, basically that codec package you have doesn't work. There are other links on this forum to the same codec package which do work.

To solve your problem try pressing ctrl and c in the terminal, that should cancel it. Otherwise just let it try to connect. I think it gave up for me on the 10th failed connection.

---

### Post by aham925925 on 2005-10-20
Ok that seems helpful...Thank You

---

