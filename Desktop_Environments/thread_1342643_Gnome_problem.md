---
title: "Gnome problem"
date: 2009-12-01
forum: Desktop Environments
---

### Post by Pharos33 on 2009-12-01
Ok so my first mistake was to let my wife use it but here we go....

  My panel at the top of the screen has the date time all the way across.  I can't get to the panel menu on it.  If i try to remove them most don't do anything.  The ones that do do one of two things: they all go away and the old panel is there and then they pop back up, or i get an error similar to this one:

 " Bad key or directory name: "/apps/panel/objects/&#65533;&#65533;&#65533;ct_5/object_type": '\250' is not an ASCII character and thus isn't allowed in key names "

I have only had this OS (ubuntu 9.10) for about a month.  I have very extensive windows experience (A+,  MSCE cert, + more) and some Linux command line exp (shell, scripting, that kinda thing) from years ago.  I've love the OS so far and plan on using it a lot more. 

I would like to be able to keep everything as is and just fix what could be causing this.  Any ideas?

---

### Post by utnubuuser on 2009-12-01
In case you fail to find another suitable solution, > cd /home/yourusername 
then
sudo rm -rf .gnome2 .gconf .gconfd .metacityfrom a recovery screen will delete all the configuration files and return you to a fresh desktop.- this also includes Evolution settings, so back-up before using.

---

### Post by nothingspecial on 2009-12-01
> **Pharos33 said:**
> Ok so my first mistake was to let my wife use it 

I have that problem too ;)

Press Alt-F2 and type gconf-editor, then navigate apps > panel

You should be able to fix it from there. Sorry but it`s getting further and further away from my gnome days so I can`t check for you.

Have you tried just deleting the panel and making a new one?

---

### Post by Pharos33 on 2009-12-01
Thank you nothingspecial that helped me figure out what is wrong.  Can't delete panel because I can't get to the panel menu.  Here's what iI figure is wrong:

in the apps/panel/objects theres an object_0 key that is mentioned in the applets section in a few applets that are double digits that are all the date/time applets

i can't seem to figure out how to get rid of them

---

### Post by Pharos33 on 2009-12-01
ok well i guess there was just about 110 instances and i was removing them because now i have them all gone thanks for the help!

---

