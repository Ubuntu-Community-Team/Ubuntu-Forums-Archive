---
title: "GNOME Do Docky"
date: 2009-03-20
forum: Desktop Environments
---

### Post by MissKitty on 2009-03-20
I've downloaded GNOME Do and I'm using it as a docky. I'll add all the shortcuts I want on it but everytime I logout or restart my computer all the shortcuts disappear. I'm sure this is not suppose to happen. Does anyone know why this is happening?

---

### Post by joey-elijah on 2009-03-20
I guess it's because no file is being written? I haven't used Gnome do for any great length of time because... : 

Do you find your Gnome do dock's animation to be slick and smooth? Mine's quite... juddery. I have a fairly capable graphics card (8500gt) that can handle HD etc so why can't it handle gnome do?!

---

### Post by Shazaam on 2009-03-20
Have you hovered your curser over either the left or right edge of Docky? It will let you expand it almost all the way across the screen. I think you will be surprised by all of the launchers already there. :)
I would guess they (your custom launchers) are still there but have been moved/re-arranged.

---

### Post by MissKitty on 2009-03-20
> **Shazaam said:**
> Have you hovered your curser over either the left or right edge of Docky? It will let you expand it almost all the way across the screen. I think you will be surprised by all of the launchers already there. :)
I would guess they (your custom launchers) are still there but have been moved/re-arranged.

I tried that but my custom launchers are not there. For the launchers I did have on there they all had their own custom icon pictures as well.

---

### Post by MissKitty on 2009-03-20
> **joey-elijah said:**
>  
Do you find your Gnome do dock's animation to be slick and smooth? Mine's quite... juddery. I have a fairly capable graphics card (8500gt) that can handle HD etc so why can't it handle gnome do?!

Mine runs very smooth. My graphics card was top of the line for laptops when I got it a year and a half ago. I'm not sure why yours is bleh.

---

### Post by MissKitty on 2009-03-21
***So does anyone know what I can do about this problem?***

---

### Post by archer6 on 2009-03-21
> **MissKitty said:**
> Mine runs very smooth. My graphics card was top of the line for laptops when I got it a year and a half ago. I'm not sure why yours is bleh.
Would you please be more specific. What make & model is your laptop? What processor? Amount of ram? Brand & model of graphics card?
Thanks.

---

### Post by MissKitty on 2009-03-21
My problem is that the lauchers on my docky disapear every time I sutdown or logout of my computer. Why is this? It's pointless for me to have this darn dock if it can't keep the launchers I put on them. How do I fix this problem?

---

### Post by SpriteSODA on 2009-03-21
The creator of Gnome Do Docky is a member of this forum. I recommend you to PM him: [http://ubuntuforums.org/member.php?u=79084](http://ubuntuforums.org/member.php?u=79084)

and I'm sure he'll be able to help you.

As for the other dude with the Geforce 8500gt, the problem is the nvidia driver.
Check out this discussion: [http://ubuntuforums.org/showthread.php?t=1095394](http://ubuntuforums.org/showthread.php?t=1095394) , some people raised this problem and he described how to solve it.

---

### Post by Ziplocpeople on 2009-03-29
I'm pretty sure gnome-do in the Intrepid repository is out-dated (it could be a bug that has since been fixed), but I'm not sure though since I'm running jaunty which has version 8.1.3, which is working fine for me.

---

### Post by xeddog on 2009-03-29
I just installed gnome-do on my Jaunty install and have only one question so far.  How do you add, or maybe more importantly for now, how do you REMOVE items from docky???

xeddog

---

### Post by Tibuda on 2009-03-29
> **xeddog said:**
> I just installed gnome-do on my Jaunty install and have only one question so far.  How do you add, or maybe more importantly for now, how do you REMOVE items from docky???

xeddog
To add launchers:
1. Search for your application using Gnome Do (Super+Space by default or click the Gnome Do launcher)
2. Click the plus icon in the lower right corner of Docky
To remove launchers:
1. Drag the launcher outside Docky.

---

### Post by MissKitty on 2009-04-16
> **danielrmt said:**
> To add launchers:
1. Search for your application using Gnome Do (Super+Space by default or click the Gnome Do launcher)
2. Click the plus icon in the lower right corner of Docky
To remove launchers:
1. Drag the launcher outside Docky.


WOW that worked! Thanks! But I have one question, how do I add a link to a website? Like I have a link to it already on my desktop but I'd like to put it on the docky.

---

### Post by ebeckhusen on 2009-04-16
> **MissKitty said:**
> WOW that worked! Thanks! But I have one question, how do I add a link to a website? Like I have a link to it already on my desktop but I'd like to put it on the docky.

You would do the same as for adding a launcher, just drag from the desktop and drop onto docky.

---

### Post by dazzlindonna on 2009-06-28
I have the same problem as Miss Kitty, although it only happens with new launchers that I add to docky. And then, once in a while, a new launcher will stick after a restart, so it's fairly inconsistent.  But "most of the time" I lose them; often enough for it to be really annoying.

---

### Post by DBO on 2009-06-30
I would need more details on how you are adding your launchers to know what internal method Docky is using to try to remember them. It's a complicated problem really =P

---

### Post by dazzlindonna on 2009-06-30
I simply drag a desktop launcher onto docky.

---

### Post by DBO on 2009-06-30
if you are dragging a launcher from your desktop and then deleting the launcher docky will "forget" about it once your delete it and restart docky because it cant find the launcher anymore.  This is fixed in 0.8.2 but if you dont have 0.8.2 you should create a folder in your home dir, call it docky-sucks, put the launchers in there, then drag them on and dont delete them.  Sorry about that...

---

### Post by dazzlindonna on 2009-06-30
Ok, that would explain it then!  Thanks, will do.

---

### Post by mayur_rathi90 on 2010-02-21
i have installed gnome do but it is not showing any docky
i.e the docky option is not available
it has only the searching do

---

### Post by Jackelope King on 2010-02-21
> **mayur_rathi90 said:**
> i have installed gnome do but it is not showing any docky
i.e the docky option is not available
it has only the searching do
Press Super+Space to summon Gnome Do, then click on the arrow in the upper right corner and select "Preferences". Under the "Appearance" tab, there should be a drop-down menu at the top of the window with the option for "Docky".

If not, perhaps you have an old build? Did you download Gnome Do from the repositories?

---

