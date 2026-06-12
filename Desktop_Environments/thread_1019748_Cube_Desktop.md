---
title: "Cube Desktop"
date: 2008-12-23
forum: Desktop Environments
---

### Post by charleskw on 2008-12-23
I have the setting for Cube Desktop turned on and everything, but how do you activate it. What buttons/keys do you press? Why do I not have a cube? I have a two sided square.

---

### Post by mshipman on 2008-12-23
Hold ctrl + alt at the same time and drag.

---

### Post by s3gfault on 2008-12-23
> **charleskw said:**
> I have the setting for Cube Desktop turned on and everything, but how do you activate it. What buttons/keys do you press? Why do I not have a cube? I have a two sided square.

you need to increase your number of desktops from 2 to 4, i guess.  This is in the system settings somewhere, idk.

---

### Post by cespinal on 2008-12-23
hold control + alt and left or right arrows. Also, pressing control+alt and down arrow will unfold the cube. 

Now, you have a two sided cube because you have only two enabled workspaces. Go to the workspace switcher, right click on it, configure it and add two more workspaces.

---

### Post by Wisp558 on 2008-12-23
Are you using compiz?

If so go to ccsm (type ccsm in terminal)

(if it doesn't work sudo apt-get install ccsm)

Go to general preferences

Go to number of desktops

Change horizontal size to 4.

Rejoice in the power of cubism.

---

### Post by blauendonau on 2011-06-01
BTW - you can middle-click on a free spot on the desktop (if your mouse has a wheel) to get the cube instead of the keyboard command.

---

### Post by ohsnap59 on 2011-06-02
I dunno, I still can't get a cube after 2 weeks of trying. ](*,)

---

### Post by 23dornot23d on 2011-06-02
@ohsnap59
What graphics card do you have ..... and what effects are working ok ?

---

### Post by stinkeye on 2011-06-02
To check if your running compiz
install wmctrl...(enter in the terminal)
```
sudo apt-get install wmctrl
```


Then run (enter in the terminal) 
```
wmctrl -m
```


If your running compiz you will get similar
```
glen@Natty:~$ wmctrl -m
Name: **Compiz**
Class: N/A
PID: N/A
```

---

