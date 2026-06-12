---
title: "Lost Gnome theme configuratioon after changing KDE look"
date: 2006-10-29
forum: Desktop Environments
---

### Post by mooha on 2006-10-29
Hi all, 

here's what happened:

I have gnome and kde installed on the system, before I had this problem, I was able to log in and out from both Gnome and Kde with no problems at all, one day I loged into KDE I changed the windows decorations and Icons colors (you know... changed the look) succesfuly works fine. so I was loging in and out from KDE without problems, yesterday I loged into Gnome I was surprised after I saw the splash screen nothing came up just the mouse I waited, nothing happened, I tried to log in again all the progress I saw was the top and bottom Bars Empty and the screen is flashing.
1- I loged into KDE again (works fine) I changed back to the default KDE theme, and went back to login to gnome, no gnome worked but with very srange themes looks.
2- If I log with a difrent user everything work fine.

Questions:

1- Is there any way I can restore back my default Gnome look ( FYI, theme manager didnt do a thing)?

2- I created a new user(everything worked fine) with this new user I have done the same thing in KDE, and I exprerianced the same problem again, why changing KDE look (themes) affected my gnome configuration?

I appologies if you see these Questions weak, I am new to Linux.

Many thanks

---

### Post by dbott67 on 2006-10-29
Take a look at this thread:
[http://www.ubuntuforums.org/showthread.php?t=288268](http://www.ubuntuforums.org/showthread.php?t=288268)

There are some settings in your home directory (they start with .gnome) that may have been corrupted.

---

### Post by mooha on 2006-10-29
Thanks for quick reply,
but the thing is ... why this files get corrupted?
and why when I created new user and changed KDE look the same thing happened?
WHY   ](*,)

---

### Post by mooha on 2006-10-30
anyone can help !!!

](*,)

---

### Post by medgno on 2006-10-30
The reason for this is that when KDE changes the Gnome themes, it creates .gtkrc files in your home directory to apply these settings. Gnome doesn't set themes this way, but instead does something else (I don't know how it works). To get rid of the settings that KDE set, there are two files you need to delete. Unfortunately, I don't remember what exactly they are named, but if in a terminal you type
```
rm -i ~/.gtkrc*
```
and only answer 'yes' to files with names like .gtkrc-2.0 or .gtkrc-1.2 or .gtkrc, it should take care of the problems you're having. (The -i switch to 'rm' tells it to ask before removing any files) You probably will need to restart programs for them to pick up on the new settings, however.

---

