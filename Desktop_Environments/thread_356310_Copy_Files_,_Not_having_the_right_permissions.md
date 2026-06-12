---
title: "Copy Files , Not having the right permissions"
date: 2007-02-08
forum: Desktop Environments
---

### Post by cfedge on 2007-02-08
Hello,

I have been using Ubuntu Edgy for about a week now.   The 1 thing I cannot stand is:

I want to copy files from my desktop to the /opt/cfusionmx7 folder but I cannot because that folder is owned by root.  so I then have to go to the command line, which is not the end of the world I do not mind it, but it is a pain.

Ubuntu does not allow me to login to the desktop with the root password.  Is there a way for me to give my user access to all directories / files without having to go to the command line and sudo or su - to root first?

Thanks!

Randy

---

### Post by tszanon on 2007-02-08
It will introduce a big security risk. I recommend: DON'T do it. But, if you don't care, you can make all files world-writeable:
```
cd /
sudo chmod -R 777 *
```
I'm not sure about the -R, but I believe it will make the command recursive.

I say again: don't do it.

Other option you have is to use groups, but I can't help you with that and I think it won't solve your problem.

Another option is to run nautilus as superuser. Type ALT-F2 and run
```
gksudo nautilus
```
While you keep the window open, it will act as if you were root (so, all write-access you need).

---

### Post by kebes on 2007-02-08
tszanon's third suggestion is the safest. Whenever you want to do some root-power copy operations, open a root version of Nautilus:
gksudo nautilus

This will open a filebrowser that has root power. Be careful, however! It's easy to make a mistake and delete something by accident!

---

### Post by cfedge on 2007-02-08
Thank you.  gksudo nautilus  is exactly what I needed.

-Randy

---

