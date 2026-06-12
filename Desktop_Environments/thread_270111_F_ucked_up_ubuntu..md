---
title: "F ucked up ubuntu."
date: 2006-10-02
forum: Desktop Environments
---

### Post by Fajitas on 2006-10-02
Hey i tried doing this
[http://www.ubuntuforums.org/showthread.php?t=219894&highlight=logitech+mouse](http://www.ubuntuforums.org/showthread.php?t=219894&highlight=logitech+mouse)
but now I cant  enter my ubuntu. I can only log in terminal and do stuff. It doesnt seems that i can do anything I'm noob here some1 help me.  thanks

---

### Post by jd65pl on 2006-10-02
What do you get if you do

```
startx
```

---

### Post by Fajitas on 2006-10-02
a lot of text and also a small message that says

fatal server error failed to initialize core devices
XIO : fatal IO error104(connexion reset by perr) on x server..

The lot of text i talked before is all saying that something failed.

---

### Post by jd65pl on 2006-10-02
Try to reconfigure your xserver using the correct driver etc.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Fajitas on 2006-10-02
is there a way to se it to default?

---

### Post by jd65pl on 2006-10-02
I'm not entierly sure if you run that command and follow the instructions it should fix your problem

---

### Post by Fajitas on 2006-10-02
my problem wasnt solved
it says 
xserver0xorg postinst warning: overwriting possibly-customized configuration file: /etc/X11/xorg.conf.20061002191127

---

### Post by timczer on 2006-10-02
In the thread you referenced, you were to create a copy of your xorg.conf file.  Did you follow this step?  If so, you should be able to copy it back using the directions listed in the thread you followed

 > sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-logi
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

You should be able to do this from the command prompt after x fails to start.

---

### Post by hulet on 2006-10-02
If you followed the instructions listed in the link you sourced in your first message here, then you must have executed the following command:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 
```

That means you have saved your original setup for X-Org so it's time to reset it.
Fist save the new xorg.conf
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.new_not_working

```
Then, restore the old xorg.conf file by executing 
```

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf 
```
Now, try to run X by typing
```

startx

```

---

### Post by Fajitas on 2006-10-02
i did the backup but its not working anyways!

---

### Post by hulet on 2006-10-02
Or, do what timcizer posted. :)

---

### Post by fragos on 2006-10-02
Clean up your language -- that's a bigger problem!

---

### Post by Fajitas on 2006-10-02
ok i did what hulet said its working now but its lagging as hell, how can i fix that?

---

### Post by bollocks00 on 2006-10-02
I was having a similar issue and I just reinstalled the whole shebang.

sudo apt-get install linux-generic
sudo apt-get install xserver-xorg

solved my problems.  No noticeable lag here.

---

