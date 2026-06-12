---
title: "Need help with XGL/Compiz"
date: 2007-07-24
forum: Desktop Effects &amp; Customization
---

### Post by arelfrost on 2007-07-24
Ok, so I installed Xgl and Compiz following the guides here on forums and need some help configuring it...

The problem is, when I login into an XGL session everything looks sort of ugly. The fonts are huge and the theme is different from the one I had before. Also, I can't change the theme. For example I had the Human theme running (with orange windows and stuff) but now everything's blue and I can't  change it. I can run Compiz with compiz --replace and all effects seem to be working fine.

I'm guessing my problem is with the XGL server. Why do all the fonts look bigger now and how come I can't change the theme? I tried changing the font settings but with no luck, everything stays the same. Everything is out of proportion now. Is there any special way to set up XGL?

Running on Acer TravelMate 6460, ATI Mobilty Radeon X1300, 1680x1050 wxga

Thanks,
Stan

---

### Post by jimminy_kriket on 2007-07-24
Did you install emerald with it? link to the guide plz

---

### Post by arelfrost on 2007-07-24
Nope, how do I install emerald? :biggrin:

And I used this one: [linky]("http://ubuntuforums.org/showthread.php?t=482773&highlight=enable+desktop+effects")

---

### Post by arelfrost on 2007-07-25
These are two screencaps, the first one is regular GNOME and the other one is XGL. So why does the second one look so ugly? And how come I can't chage the way it looks?

[[IMG]http://img526.imageshack.us/img526/2860/gnomewe9.th.jpg[/IMG]](http://img526.imageshack.us/my.php?image=gnomewe9.jpg)

[[IMG]http://img526.imageshack.us/img526/9708/xglwx8.th.jpg[/IMG]](http://img526.imageshack.us/my.php?image=xglwx8.jpg)

---

### Post by Espreon on 2007-07-25
I had that prob too but it can be remedied with a simple shell script:

Edit: since the Beryl wiki is closed for a while since a bunch of DHs have been defaceing it (I have been fighting the wiki spam myself and the WayBack machine is not working I will tell you when I find out the anti-crapifing command.

First go to your home folder and make a folder, lets call it .shellscripts
Make sure you can see hidden stuff, if not configure Nautilus to do so.
Now enter the folder.

---

### Post by arelfrost on 2007-07-25
I have just solved the poblem. All I did was to replace the contents of startxgl.sh with the ones suggested here: [link]("https://help.ubuntu.com/community/CompositeManager/Xgl?highlight=%28composite%29") and now everything looks the way it should. :)

Thank you for your help, though! ;)

---

