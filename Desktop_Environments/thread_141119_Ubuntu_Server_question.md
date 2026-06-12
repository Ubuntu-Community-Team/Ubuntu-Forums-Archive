---
title: "Ubuntu Server question"
date: 2006-03-07
forum: Desktop Environments
---

### Post by stabface on 2006-03-07
Not sure if this is the right forum but I need some help

I have been a big fan of Ubuntu since i got my laptop and installed ubuntu and everything worked out of the box. 

So at the office there are 14 windows pc's and a windows server runner windows server 2003 i was asked to set up a second back up server. I of course grabbed the old P3 from the closet and added 256 of ram(all i had) and through Ubuntu in server install half an hour latter was adding users and putting it away. I was fine with this it was ok for me, using putty to control and edit everything is fine with me. But I was asked if there was a GUI for the server so it would be easy for the people in the office. I have no Idea about this, is something that is nice looking that I could set up so i can convince them to get rid of the windows 2003 server.

---

### Post by taurus on 2006-03-07
Even you installed a server, you still can install Gnome or XFce4...  To install Gnome, run
```

sudo apt-get install ubuntu-desktop
sudo apt-get install xubuntu-desktop (for Xfce4)

```

---

### Post by SlowHorse on 2006-03-07
To implement a GUI from across the network (I would personally recommend Xfce in your case), install the vncserver package:

sudo apt-get install vncserver

---

### Post by shamrock_uk on 2006-03-07
If all you want to do is long into a remote account on the server, then I can't recommend [FreeNX](https://wiki.ubuntu.com/FreeNX) highly enough. Blows VNC out of the water in terms of speed.

---

