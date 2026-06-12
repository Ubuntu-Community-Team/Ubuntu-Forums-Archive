---
title: "Programs suddenly starts up slow"
date: 2007-10-02
forum: Dell  Ubuntu Support
---

### Post by trondhuso on 2007-10-02
Hi list,
Suddenly my programs (and Gnome) starts up really slow. I haven't timed it but things doesn't go that fast.  It used to earlier today, and so I might kinda know what caused it, but I changed that.

What I suspects might have caused it is that I connected the computer to my jobs network and added it's domain. But I took that away from network settings. 

That did not help much. I have also checked System monitor, but I haven't checked any logs as I don't know what to look for or where. 

Any suggestions are welcome.

My computer is a Dell D420. OS is Ubuntu Feisty

-t-

---

### Post by ridgeland on 2007-10-02
Networks have caused major slow downs for me.
I took NFS out of /etc/fstab because if the other PC was off then boot suddenly turned to way way slow.
I also find that if I have NFS to another PC and that PC gets turned off then nautilus can take very very very long to load.  
I only connect to NFS with a small script and disconnect with a small script when done.  I don't leave it on when not needed.

---

