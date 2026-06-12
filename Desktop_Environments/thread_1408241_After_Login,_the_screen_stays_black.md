---
title: "After Login, the screen stays black"
date: 2010-02-16
forum: Desktop Environments
---

### Post by MicroBoy on 2010-02-16
It is happening for the second time, after I installed Ubuntu 9.04 on my PC, I deleted some packages usually some applications packages, like bluetooth packages, printer packages, ekiga, evolution etc... (using Complete Removal). Everything seems good until I shut down my PC, when I want to turn on, it run OK until I have to write the Username and Password then I just can see a black screen with mouse on it, I can move the mouse but nothing else is displayed. Is there any way to solve this unless Installing it again. Maybe the packages aren't the issue at all?

---

### Post by mimor on 2010-02-16
What dependencies did it remove with it?
I can imagine there is a huge part of the gnome environment clogged together with evolution etc.

You might want to reinstall gnome.
Press Ctrl-Alt-F2 
Log on
Enter:
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by MicroBoy on 2010-02-16
I really don't know maybe it removed some packages that I didn't know because I clicked "COMPLETE REMOVAL", is there any way to install gnome from CD, just GNOME, because from Internet it will take a long time, cause my internet connection isn't to fast.

---

### Post by mimor on 2010-02-16
You can add the cd-rom as a repository by doing:
```
sudo apt-cdrom add
```

---

### Post by MicroBoy on 2010-02-16
So then the system will know that the best way to install gnome it's CD and get automatically from CD? By the way where to do this things because I can't use Terminal I can't log in to Ubuntu?

---

### Post by mimor on 2010-02-16
First you boot up ubuntu.
Second you change runlevel by hitting Press Ctrl+Alt+F2 
Then you will be presented with a full-screen terminal :)
There you can log on and enter the commands.

You might want to pull out the network cable so apt gets everything from the cd (as it won't be able to contact the mirrors)
You can stop the networkservice with:
```
sudo service network stop
```

---

