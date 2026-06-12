---
title: "Resolution Issues"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by Xephrey on 2007-05-27
I've been on my Dad's machine, and a problem with the resolution not sticking to what I set it as after a restart has come up. I would like it to stay as 1280 x 1024, but after every restart, it goes back to 1024 x 768. This has come up a few times before while I was working on my own system, and I wasnt sure how it was solved. I click the 'save to xconfig' button on the nvidia settings, but it doesnt seem to do any good. 

Any help would be greatly appreciated. 

Thanks! :)

---

### Post by spin2cool on 2007-05-27
Try editing your xorg.conf file by hand.

Back it up first, so you can roll back changes if you mess something up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Edit the file
```
sudo gedit /etc/X11/xorg.conf
```
Find the section that contains the listing of resolutions, and add your desired one to the front of the list, using the same format.  Save the file, and reboot (or restart your X-server).

---

### Post by Cresho on 2007-05-27
just remember that the highest set resolution on the xorg.conf will be what the desktop starts up at.

---

