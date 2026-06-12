---
title: "KDE wont let me go back to Gnome"
date: 2006-04-10
forum: Desktop Environments
---

### Post by krypto_wizard on 2006-04-10
I was a Gnome user and  tried to use KDE for sometime. I also installed kubuntu-desktop.

Now I want to go back to gnome as I liked it more. KDE wont let me login to Gnome.

When I choose the session gnome and give username and password, it just hangs after a while. I think my graphical manager is now kdm instead of gdm.


How can I have a smooth system where I can easily switch between gnome and kde.

please help me get gnome back.

---

### Post by eriefisher on 2006-04-10
Even if KDM is the default selecting Gnome in the session menu should start GDM. You can always set wich one you want as the default. Can you try to log into text and try to start GDM?

eriefisher

---

### Post by krypto_wizard on 2006-04-10
How to start the gdm ? 

Which  file I need to access ??

[QUOTE=eriefisher]Even if KDM is the default selecting Gnome in the session menu should start GDM. You can always set wich one you want as the default. Can you try to log into text and try to start GDM?

eriefisher[/QUOTE]

---

### Post by Qrk on 2006-04-10
You can reconfigure kdm with

```

sudo dpkg-reconfigure kdm
```

or use that tool to select gdm if you so desire. 

I'm afraid I don't have kdm installed, so I won't be much further of a help.

---

### Post by krypto_wizard on 2006-04-10
how can i win back my gnome ?

---

### Post by eriefisher on 2006-04-10
Try what Qrk suggested but replace kdm with gdm. That should restart Gnome.

eriefisher

---

### Post by krypto_wizard on 2006-04-10
That didnt work!!


[QUOTE=eriefisher]Try what Qrk suggested but replace kdm with gdm. That should restart Gnome.

eriefisher[/QUOTE]

---

### Post by aysiu on 2006-04-10
You could also try ```
sudo /etc/init.d/kdm stop
sudo /etc/init.d/gdm start
```

---

### Post by diffuser78 on 2006-04-10
deleted

---

### Post by krypto_wizard on 2006-04-10
Now I can see the yellow/brown gnome login scree, but after giving username and password and selecting GNOME it crashes. It just hangs there and nothing happends with brown screen. Then I trying logging to KDE and I can do that.

How to recover gnome ?

[QUOTE=aysiu]You could also try ```
sudo /etc/init.d/kdm stop
sudo /etc/init.d/gdm start
```[/QUOTE]

---

### Post by krypto_wizard on 2006-04-10
Is it a good idea to more to dapper since i am having all these troubles ??

---

### Post by krypto_wizard on 2006-04-10
Shall I download gnome once again to  put gnome on top ??

---

### Post by aysiu on 2006-04-10
I don't know what you should do, to be honest.

---

### Post by krypto_wizard on 2006-04-12
KDE wont let me go into GNOME. Gnome crashes while starting. And all I see is a brown screen.

Please help me to fix this problem.

---

