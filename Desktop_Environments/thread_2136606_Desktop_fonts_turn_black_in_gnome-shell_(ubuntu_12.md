---
title: "Desktop fonts turn black in gnome-shell (ubuntu 12.04)"
date: 2013-04-18
forum: Desktop Environments
---

### Post by rrich1974 on 2013-04-18
last night i installed gnome-shell from official repository, it works fine but i encounter a small problem: i have noticed that the fonts of the desktop icons have suddenly turned black...the initial colour was white. i am using gnome-shell 3.4. 
i have had the same problem while using gnome shell in fedora 17 (previous year)....i think the problem is embedded in gnome shell. i don't have this issue in unity 3D. 
a logoff and log back in solved the problem. 
other than that, gnome shell woks damn good! i love it! 
what can it be? 

PS. i will post a screenshot as soon as the issue will appear again! thanx!

---

### Post by rrich1974 on 2013-04-21
now, the title bar of the windows are black...as you can see in the screenshot.

---

### Post by Frogs Hair on 2013-04-21
I have seen this in the Gnome Shell only when mixing themes, meaning the title bar theme is different from the GTK theme. It does not occur with all themes though.

---

### Post by rrich1974 on 2013-04-21
but i can tell you that i did not change a thing. i just installed gnome shell from USC in ubuntu 12.04 unity.

later edit:
honestly, i am afraid to install gnome-tweak-tools and change tha theme because i dont know how this will interfere to unity.

---

### Post by sammiev on 2013-04-21
I use gnome-tweak-tools and had no issues with gnome-shell or unity.

---

### Post by rrich1974 on 2013-04-21
thanx o lot man, but i ask you, if you change a theme in gnome shell, how that change will affect unity?

in the end, after i installed gnome-tweak-tool it seems that when you change the theme in gnome-shell it also change in unity.

---

### Post by Frogs Hair on 2013-04-21
Unity will share themes with the gnome shell and vise versa . Restarting the shell will sometimes help after a theme change if the theme is not displying properly. Alt + F2 ```
r   
``` If you download and install themes make sure they are compatable with your version of the shell, in 12.04 that would be 3.4.

---

### Post by sammiev on 2013-04-21
Here is another screen shot but using unity with the same settings as gnome-shell using FF20 and FF23 in reverse order this time from my last shot.

---

### Post by rrich1974 on 2013-04-23
yesterday, i changed the theme from ambiance to adwita (default gnome)....so far, it works good. i look forward to see what is going on in the next days!

---

### Post by rrich1974 on 2013-04-24
today, the problem strikes again.....i am pretty sad because i really like gnome shell. it seems that unity is much more polished than gnome-shell. as you can see, i use default theme!

later edit: 
it seems that playing with antialiasing setting solved the problem, without restarting shell, i have set it on grayscale.

---

### Post by richardsdma on 2013-10-15
now, after all this time, the problem still persists. 
even if i use gnome shell installed over ubuntu 13.10 (gnome 3.8). 
it seems the same problem as it is presented here....i forget to tell you about "chopped" fonts. 
[https://bbs.archlinux.org/viewtopic.php?id=148537](https://bbs.archlinux.org/viewtopic.php?id=148537) 
this guy have the same problem and it also has a mobility radeon video card (mine is x1270) 
after all, it seems that the problem is specific to ati video cards.

---

