---
title: "White backgroung of icons in system tray"
date: 2010-11-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by geaden on 2010-11-04
Hello, everyone!

On my Dell Vostro 500 with Ubuntu 10.10 installed there is a problem. Here is the picture:

[IMG]http://img821.imageshack.us/img821/247/strangeicons.gif[/IMG]

White background of icons of some software. Are there any solutions of that?

Thanks.

---

### Post by cipherboy_loc on 2010-11-04
The only way to fix that that I know of is to use GIMP (sudo apt-get install gimp) to change the background color for all those icons (you will need to find them) to alpha-colored (transparent). 

There are a few ways to do this: 

1) Under Colors, click on Color to Alpha. Make sure the color is white, and click Ok.
2) Use the Select by color tool (In the toolbox, in the top row, its the one to the far right (With the hand pointing to the red box)), click on white and then hit delete. 
3) Use the fuzzy select (Top row in the tool box, the one with the wand), select the white area(s) and press the delete key. 

Save and exit.


Also remember to use sudo to launch gedit (or gksudo if not running from the terminal).






Cipherboy

---

### Post by geaden on 2010-11-25
Thanks **cipherboy_loc** for your answer and step by step instruction. Where can I find the locations of that icons?

---

### Post by hawthornso23 on 2010-11-29
I think you'll find that the background of those icons is already transparent. This is a longstanding bug in gnome - and by longstanding I mean this bug has been around for YEARS. 

Open  system > preferences > appearance
click on 'customize' then open the 'colors tab.
Change the color for the Windows Background. You'll see the icon background change to match. 

Somehow and only in some applications, when a transparent icon sits on a transparent panel the color is set inappropriately to the window background color. It is said that the problem only exists in some themes and you can sometimes get rid of it by changing theme, but I have not observed this for myself.

Launchpad is full of bug reports on this issue. My guess is that it shows up only when the applications don't do things in precisely the way gnome expects. But quite a few applications are afflicted with this problem. There is no chance that the gnome people will fix  this. The `system tray' is regarded as obsolete by the gnome developers  and is due to be phased out in future versions of gnome.

---

