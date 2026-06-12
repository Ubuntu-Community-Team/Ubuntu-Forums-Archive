---
title: "Gnome doesn't work, but xfce does"
date: 2012-01-29
forum: Desktop Environments
---

### Post by l07 on 2012-01-29
I was trying to to use ubuntu hard drive on another pc (2), but couldn't get the graphics to work. I was only using gnome on 2. Since it didn't work, I moved the drive back to 1, but the newly created problem came back with the drive. Eventually I logged in with xfce, which worked and was able to restore the proper resolution, but logging into gnome (also into safe mode) doesn't seem to work well: the mouse moves but cannot click anything, the resolution is still low (it is also low before logging in), the keyboard doesn't seem to work in gnome, but can switch to other virtual terminals.

How to fix gnome?

---

### Post by l07 on 2012-01-30
**Gnome still doesn't work.**

---

### Post by 3Miro on 2012-01-30
What is the video card and which driver are you using?

You may have to reinstall the proprietary video driver. Go into XFCE and check with Additional Drivers. To properly reinstall the driver, you should first deselect it, reboot, select it again and then reboot again.

---

### Post by l07 on 2012-02-26
NV17 [GeForce4 MX 440] (rev a3)
driver: 96.43.19 (recommended)

Reinstalling the driver didn't seem to help.

---

### Post by 3Miro on 2012-02-26
This is an old video card. Only gnome-fallback (I think they called it Gnome-classic) has some chance of working, but make sure to disable any effects like transparency.

There may be a way to adjust some setting to work with Gnome, you can try to search the forum for your video card (GeForce 4), but I don't know how. This may just be a bug in Gnome, I doubt they have tested it on GeForce 4. If I were you, I would just stick with xfce, it is more suitable for old computers and it will probably work better.

---

### Post by l07 on 2012-02-26
But I had gnome working before. It was working perfectly fine and I didn't change any settings within it.

---

### Post by 3Miro on 2012-02-27
Maybe some local Gnome setting got messed up. Here is one way to check, make a new user and login with that user under Gnome. If you can login with the new user and everything is working fine, then you should just reset your Gnome settings. Basically delete some folders that start with ., like .gconf and .gnome2, I have to double-check for the full list.

---

### Post by |{urse on 2012-02-27
-Ignore this-

---

### Post by l07 on 2012-02-28
I haven't yet tested your suggestion, and in the meanwhile I have the following question, which would save me from having to restart.
Usually I would switch to another virtual terminal when gnome's not working and type a command there to restart, since I don't know how to start another window manager from command prompt in the current terminal. How to do so? Alternatively, if I don't switch to another terminal, how to make gnome log off so I can login to xfce?

---

### Post by 3Miro on 2012-02-29
To quit Gnome:
```
gnome-session-quit
```

To restart the entire graphical environment (without rebooting the machine):
```
sudo service lightdm restart
```

To restart just the windows manager (assuming you are using classic session):
```
metacity --replace
```

---

### Post by l07 on 2012-03-04
Gnome works under a new user. Which folders need to be deleted?

---

### Post by 3Miro on 2012-03-05
From the new user, start Nautilus with super user powers from the terminal:
```
gksudo nautilus
```

Then go to the folder "/home/old_user_name". Then hit Ctr+H to see all the hidden files. You will have to delete anything .gnome or .gconf or .metacity or .compiz. You should then go into the folder .config and do the same including deleting .nautilus (do not delete everything in .config, just the gnome stuff). After you delete everything, you should be able to login with the old user, but your settings would be lost (your files would be there).

---

### Post by l07 on 2012-03-17
That fixed it, thanks.

---

