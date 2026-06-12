---
title: "Install Gnome on Server"
date: 2008-03-14
forum: Desktop Environments
---

### Post by RandomUsr on 2008-03-14
> sudo apt-get install ubuntu-desktop

that line give me and error and 

E: couldn't find package

How can I get gnome w/o going through the CD rom which doesn't work right?

---

### Post by Dr Small on 2008-03-14
Run:
```
sudo nano /etc/apt/sources.list
```

And uncomment the cdrom:// entry.
If all of the rest of the entries are commented out, uncomment them.

Now run:
```
sudo apt-get update
```

Dr Small

---

### Post by RandomUsr on 2008-03-16
```
xauth: creating new authority file /home/CurrentUser/.serverauth.4850
xauth: /home/CurrentUser/.Xauthority not wrietable, changes will be ignored
xauth: error in locking Authority file /home/CurrentUser/.Xauthority
cannot read from /etc/X11/X Symbolic Link [invalid argument], aborting 
xinit connection refused [errno 111]: unable to connect to xserver
xinit no such process [errno 3]: Server Error
xauth: error in locking authority file /home/CurrentUser/.Xauthority 
```

I get this code after running startx
Any ideas

---

