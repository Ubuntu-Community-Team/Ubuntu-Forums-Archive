---
title: "Screen Resolution problum"
date: 2006-01-17
forum: Desktop Environments
---

### Post by tophat2445 on 2006-01-17
OK, I just started using Ubuntu, its a great OS! But I have a problum, My screen resolution is at 640x480. THATS TOO BIG!.  I went to System -> Screen Reslution, but I cant change my resoluiton.  

Can I fix this? I would like to get a resolution of about 1024x786

---

### Post by crispy_420 on 2006-01-17
configure xorg to allow more options?

---

### Post by byen on 2006-01-17
Ok. see if this helps.
First Please backup your xorg.conf file ,just incase this does not work.
Command to backup xorg: Open terminal and type
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

After doing this.. type the following command to open a graphical screen using which you can configure your system to suit its hardware:
sudo dpkg-reconfigure xserver-xorg

In one of the options you get to choose the resolution that you would like xorg to load.
Hope this helps. Goodluck.

---

### Post by byen on 2006-01-17
Note: Just incase your xorg fails to load up properly and you get a text-boot during restart . Do this:
login with your user name and password <enter>
Insert code:
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

Let us know if you have any trouble. Just realized that this is your first post.... Welcome to Ubuntu!

---

