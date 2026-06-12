---
title: "Duel Screen Issue"
date: 2011-07-19
forum: Desktop Environments
---

### Post by unhopeful on 2011-07-19
I tried to set up duel screen with the Nvidia server and when i restarted my main screen was black and my second screen ( 32" LCD TV ) was zoom'd away in to the top left corner of my dest top.

Are there any Terminal commands to reset the setting back ?

---

### Post by unhopeful on 2011-07-19
Right peep's really need to sort this issue out.

---

### Post by unhopeful on 2011-07-20
Bump !

---

### Post by madfrog on 2011-07-20
I feel your pain!

I am having a lot of problems with a multi-screen setup  myself


Check if there is a backup of your xorg.conf file in /etc/X11/

```

ls -l /etc/X11

```

Replace the current xorg.conf with the backup
```

sudo cp /etc/X11/name.of.backup /etc/X11/xorg.conf

```


If not, try 
```
sudo nividia-xconfig
```


If you make any changes to xorg.conf you have to restart your display manager.

You can stop and start the display manager (for testing) by doing the following:

alt+F1 for terminal
alt+F8 should bring you back to graphical display

in terminal 

for gnome
```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```

---

