---
title: "Removing bad graphics driver"
date: 2009-05-14
forum: General Help
---

### Post by Teutorix on 2009-05-14
I installed a graphics driver yesterday and now my screen displays nothing after i boot up.

It was the driver recommended by ATI for my Radeon xpress 200.

Is there a way to revert my settings through recovery mode or something?

---

### Post by 3rdalbum on 2009-05-14
When you get the blank screen, press Control-Alt-F1 to switch to a virtual terminal.

Edit the Xorg.conf file:

```
sudo nano /etc/X11/xorg.conf
```

Where it says "Driver:    "fglrx"" change the "fglrx" to "ati".

Save changes and quit by pressing Control-X, Y, and Enter. Then reboot by typing:

```
sudo reboot
```

---

### Post by Teutorix on 2009-05-14
when i do that im just getting the GNU nano 2.0.7 interface but no text appears and it says [ NEW FILE ] at the bottom

---

### Post by rcayea on 2009-05-14
Maybe try booting to safe mode and using the command line to do those instructions as posted. 

Or, I also think in safe mode there is an option to fix the graphics card.

---

### Post by Teutorix on 2009-05-14
i tried it in safe mode, and i tried the recovery mode fix tools, still nothing.

is there a command to reset the system? I'm not worried about loosing files, its my 5th time in two weeks something like this has happened

---

