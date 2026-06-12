---
title: "editing themes..."
date: 2006-08-07
forum: Desktop Environments
---

### Post by Trab on 2006-08-07
hello, im wondering if someone can give me advice about editing a specific part of a tmeme. im using greenheart for my controls, and i love it, but it makes alot of text in firefox white on white (For example what im writing right now...) as well as what is in gmail.
this is very frustrating and difficult and i was wondering where do i need to edit the hex code to fix it?
cheers,
Trab

---

### Post by ahaslam on 2006-08-07
I've not experienced that problem before. All I can suggest is that you go to the theme folder in /home/.themes/
Open up the gtkrc file and have a look for background/font/toolbar colours.

Tony.

---

### Post by soulmatic09 on 2007-12-16
i made a post on editing themes that you may want to look at:

[http://ubuntuforums.org/showthread.php?t=642636](http://ubuntuforums.org/showthread.php?t=642636)

i had the same problem with a theme i edited, only it was black text on a black background.


what I had to do was edit the gtkrc file of the GTK theme, and edit the background color in the menu section. Try that, and see if it works.

---

