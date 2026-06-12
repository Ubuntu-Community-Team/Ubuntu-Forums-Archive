---
title: "SSH Problems Feisty 7.04"
date: 2008-07-24
forum: Desktop Environments
---

### Post by matey3 on 2008-07-24
Hello All:

I am not sure what kind of problem this is (I do not know why or how it happens) But when I am in my GUI (gdm) environment the SSH will NOT work after a while? 
SSH Works great when I have just loggd into my GDM (Nautilus desktop)but after while It will not work. 

After I am on a few hours then I can still creat links to other servers in my network but after while when I double-click them this little window comes up and says "If you dont want to wait hit the cancel.."etc.
when this pop up come up I can never log into any remote servers until I reboot again?!

Then if I have the computer on for a day or so I cannot get into local folders/drives the same way?
I thought may be it is FireFox? But I am not so sure now since everything works great with firefox opened after a fresh restart?

anyone seen this happen before?

Thanks very much in advance.

---

### Post by theophile on 2008-07-24
It's hard to tell from your description what you're trying to do, but if you're trying to persistently mount remote filesystems, you should use NFS rather than SSH (which is not meant for that).

---

