---
title: "DISPLAY shows the wrong IP"
date: 2009-02-25
forum: General Help
---

### Post by smackdaddymack on 2009-02-25
I am running ubuntu on a virutalbox installed on my XP machine.  The IP of my XP machine is xxx.xxx.xx.41 

The problem is when I ssh over to my server and do a 
echo $DISPLAY it shows me as xxx.xxx.xx.43  

I did an xhost + serverip  before sshing over to the server.

When I then try to bring up a xterm I get a 
xterm Xt error: Can't open display: xxx.xxx.xx.43
next
setenv DISPLAY xxx.xxx.xx.41:0.0
echo $DISPLAY
xxx.xxx.xx.41
xterm


At first it then acts like the xterm opened correctly but it does not
pop open an xterm in my virtualbox.
Then after a long pause I get.
xterm Xt error: Can't open display: xxx.xxx.xx.41

This is a new install and the only thing I have done is add my server name and ip to the hosts file.


Any ideas?
Thanks,
-B




********** Never mind I had the DISPLAY set wrong in .my.cshrc on the server.  Thanks anyway ************

---

