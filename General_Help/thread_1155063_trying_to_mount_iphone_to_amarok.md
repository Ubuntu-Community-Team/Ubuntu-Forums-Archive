---
title: "trying to mount iphone to amarok"
date: 2009-05-10
forum: General Help
---

### Post by rreyes1316 on 2009-05-10
These are the comanda I have tried to enter. However when I enter the last line I get  an error. 

sudo mkdir /media/iphone/ -m 777
sshfs root@192.168.1.132:/var/root/Media /media/iphone/
ln -s iTunes_Control /media/iphone/iPod_Control
fusermount -u /media/iphone

This is the error.ntry for /media/iphone not found in /etc/mtab. As a newbie I am not sure how to solve this, Here is the istrucions page I have been trying to follow. [http://blog.adaniels.nl/articles/iphone-amarok/](http://blog.adaniels.nl/articles/iphone-amarok/)

---

### Post by 987poiuytrewq on 2009-05-11
Try downloading the package ipod-convenience this gives an easy way to correctly mount your iPhone.

---

