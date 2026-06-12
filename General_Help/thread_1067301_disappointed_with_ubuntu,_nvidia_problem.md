---
title: "disappointed with ubuntu, nvidia problem"
date: 2009-02-11
forum: General Help
---

### Post by saied45 on 2009-02-11
hello all. i always have heard such great stories about ubuntu  yet i have had no luck with it. i downloaded the latest version 8.10. the biggest problem i have with ubuntu is my problem with nvidia. i have an compaq laptop cq 60-210us. 
i have  major problems. which i believe are caused by the drivers.
first problem is that each time after installing nvidia drivers either 173, 177, or 180 i get this weired garbled screen during shutdown. it is not a huge problem yet its annoying.
the second problem im having is firefox gets garbled text while i scroll up or down. i disabled smooth scrolling and that almost solved it yet i still get garbled text time to time. i downloaded opera which solved all the problems of garbled text yet some of the videos online from some sites are extremly choppy but they are fine in firefox.
but the garbled text is not only in firefox but also pidgin. when ever i do a full screen the garbled text appears and i have to click on the text to get it ungarbled.
so far i like somethings off ubuntu yet the major problems im having is for it to work. if someone can help me i appreacite it.

---

### Post by bodhi.zazen on 2009-02-11
First you need to be clear as to who is at fault.

You should direct your nvidia frustration to nvidia. The nvidia drivers are closed source and thus are maintained by nvidia, not the ubuntu developers.

---

### Post by mc4man on 2009-02-11
It would be interesting to see what nvidia adapter you have in there, this should tell
```
sudo lshw -C display
```

---

### Post by saied45 on 2009-02-11
its an 8200 M G. i installed MINT too and still i got the same problem. i think its all nvidia. but anyone know a workaround with this problem. what i dont understand is why is there no garbled text with opera?

---

### Post by resolv3 on 2009-02-12
Hey, I have a Compaq CQ60-215dx. I also experience text that is too close together, when I try to play games the refresh rate is horrible. When in the file system like browsing for a file a app is asking for, it will either show the default one or a plain white box where icons would be. The icons are still there. you can click on them and change directories, and select files. The screen doesn't change though so I have no idea what im clicking on.

This is very iritating. Other than the poor Gfx driver my experience with Ubuntu has been great.

---

### Post by jerome1232 on 2009-02-12
In all honesty nvidia is who develops the driver and they have a linux support forum, might want to try that.

[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by mc4man on 2009-02-12
It's actually fairly remarkable that linux is able to support the range of notebook display adapters that it does.
On the windows side ati and nvidia aren't responsible for notebook adapters, it's left up to the individual manufacturer to release drivers specific to each model.

On a positive note you have a 8200 which I don't believe is included in the list of potentially defective chips (almost all 8400 and 8600 chips are.

[http://www.engadget.com/2008/07/31/figuring-out-which-nvidia-gpus-are-defective-its-a-lot/](http://www.engadget.com/2008/07/31/figuring-out-which-nvidia-gpus-are-defective-its-a-lot/)

---

### Post by saied45 on 2009-02-13
actually i managed to solve the garbled text problem. what i did was first install a new fresh ubuntu, then updated the kernel and everything else, THEN i installed the newest version of nvidia drivers and that seams to have solved the problem. i got a new problem tho and i believe its ubuntu. when i try to install wine and i go to system-administration-software source and authentication and click import key file, my ubu freezes. anyone know WHY? im trying to install wine and thats the directions

---

