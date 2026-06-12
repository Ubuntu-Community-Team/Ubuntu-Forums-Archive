---
title: "Disabling screen saver in XFCE"
date: 2019-09-23
forum: Desktop Environments
---

### Post by hk42 on 2019-09-23
How do I do that ?
After exploring the huge "settings" menu I didn't find this option.
So very often my screen gets blank and the TV used switches off and getting everything back is very time consuming.
Also if I switch to a text console my password is asked when going back to graphic mode.
Thanks for your help.

---

### Post by Dennis N on 2019-09-23
First thing to try:

Check settings in Settings > Power Manager > Display Tab
Display Power management Switch > On
Settings:
Bkank after: never
Put to Sleep: never
Switch off: never

---

### Post by hk42 on 2019-09-23
Believe it or not I have no less than 29 entries in the settings menu.
But no trace of power manager

---

### Post by uRock on 2019-09-23
What install method did you use? You "should" be able to find it in one of two places.

---

### Post by ajgreeny on 2019-09-23
And which screensaver are you using?

I think Xubuntu uses xscreensaver, so there should be a window where you can choose to disable it in a dropdown box as in my screenshot.

Note in the screenshot it shows my own setting of use "Only one screen saver"

---

### Post by #&amp;thj^% on 2019-09-23
To pull up what the others are showing you use:
```
xfce4-power-manager -c 

```
Then follow what they suggested. :)

---

### Post by Autodave on 2019-09-23
You may need to install power manager.  It is in synaptic and probably the software center.  You need:  
xfce4-power-manager

---

### Post by hk42 on 2019-09-23
Yes I installed XFCE over the normal gnome of 19.04 with apt-get install XFCE.
I have no dedicated screen saver (I hate them).
Apart from this all went well and I have a nice login menu where I can choose user and GUI.
From your above screen captures I realised that I have a few icons missing in the hardware section.

---

### Post by uRock on 2019-09-23
> **hk42 said:**
> Yes I installed XFCE over the normal gnome of 19.04 with apt-get install XFCE.
I have no dedicated screen saver (I hate them).
Apart from this all went well and I have a nice login menu where I can choose user and GUI.
From your above screen captures I realised that I have a few icons missing in the hardware section.

That puts it into perspective. Give autodave's advice a try. That'll get the Power Manager installed and hopefully help get rid of the issue.

---

### Post by #&amp;thj^% on 2019-09-23
I agree with uRock, but I'm not sure the screensaver is in play here> might be a screen-lock issue. And I've never seen XFCE4 installed with-out Power-manager included. 
If this persists use this once.
```
xset s off
```

---

### Post by hk42 on 2019-09-23
> **uRock said:**
> That puts it into perspective. Give autodave's advice a try. That'll get the Power Manager installed and hopefully help get rid of the issue.
Thanks .I did that and I now have the missing icon in the hardware section.It seems to work.

---

### Post by uRock on 2019-09-23
Awesome! Don't forget to click on thread tools in the upper right and mark this thread solved.

---

### Post by Autodave on 2019-09-23
I run Xubuntu on 10+ machines here.  The last LTS that I remember having Power Manager when installed is 14.04.

---

### Post by hk42 on 2019-09-24
It definitely works.
Thanks to all .This forum is impressive.

---

