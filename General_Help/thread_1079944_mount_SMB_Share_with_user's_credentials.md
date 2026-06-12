---
title: "mount SMB Share with user's credentials??"
date: 2009-02-24
forum: General Help
---

### Post by johnson8707 on 2009-02-24
Alright, so here is the environment:

I am trying to incorporate Ubunutu/Xubuntu machines into a windows network. I have gotten the machines to join the domain using Likewise open. I would like for the user's home folder (on an SMB Share) to be mapped and for the share to be mounted with the users login credentials (so the user can't access others files)


Here is what I am guessing:
I've tried to configure Samba with no luck. I have desperately searched the web and found PAM_Mount to be the only thing close to what I need for this. But have not found any guides on how to use it.


If anyone can help me out with this I would be VERY grateful!

THANKS A LOT!!! :)

---

### Post by Nano_ext3 on 2009-02-24
Try searching for "add windows share to linux"

See:  [http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html)

Also:  SMB method:  [http://www.cyberciti.biz/faq/access-windows-shares-from-linux/](http://www.cyberciti.biz/faq/access-windows-shares-from-linux/)

Hope this helps you m8

Cheers!

Nano

---

### Post by johnson8707 on 2009-02-24
I've actually done many searches similar to that and stumbled across those 2 exact pages before. :)

The problem is that I need it to be automated. Because the users who logging into these machines will probably be experiencing Linux for the first time. So I need to set it up to where it functions similar to all the Window's machines on our network.

Appreciate it though! :D

---

### Post by johnson8707 on 2009-02-24
Anyone else have some ideas??

---

### Post by johnson8707 on 2009-02-25
Anyone???

---

