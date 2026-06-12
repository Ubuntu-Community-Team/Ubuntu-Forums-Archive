---
title: "Gnome-menu"
date: 2005-07-15
forum: Desktop Environments
---

### Post by fnando on 2005-07-15
Hi again!
I did something wrong with the top gnome-menu and guess what? It disappeared!
How do I restore the previous one or create a new one?

Thanx!!!

---

### Post by jasmuz on 2005-07-15
Left click on top of the bar, Add to pannel, and choose the Menu bar applet.
That's it-

---

### Post by fnando on 2005-07-15
[QUOTE=jasmuz]Left click on top of the bar, Add to pannel, and choose the Menu bar applet.
That's it-[/QUOTE]

Oops! No bar at all on my screen!!!

I installed smeg... I can see the menu when I run smeg through Terminal.... but I don't know how to add the whole top menubar....

---

### Post by endy on 2005-07-15
Perhaps if you run "gnome-panel" from a terminal you can carry on from there :)

---

### Post by fnando on 2005-07-15
Great!!! And easy!!!

Just one more question... When I close the terminal, the bar closes too... how to keep enabled on boot?

---

### Post by Caboto on 2005-07-15
Hmmm.... Alt+F2 -> gnome-panel should do it. Remember to save your session, when you logout.

---

### Post by fnando on 2005-07-15
OK... When running gnome-panel gives the error below:

> I've detected a panel already running,and will now exit.

---

### Post by Omnios on 2005-07-15
Had something similar happen there is a local menu config file /home/..user../... that sets up the menu

 You could try renaming the file with backup on the end of it and log in and out. When I did it it defaulted back to the original settings. Be shure to back it up "do not delaet it" If it does not work rename back to the original name. Its kind of harsh but it worked for me.

[My Original Menus post](http://ubuntuforums.org/showthread.php?t=41213)

---

### Post by fnando on 2005-07-15
[QUOTE=Omnios]Had something similar happen there is a local menu config file /home/..user../... that sets up the menu

 You could try renaming the file with backup on the end of it and log in and out. When I did it it defaulted back to the original settings. Be shure to back it up "do not delaet it" If it does not work rename back to the original name. Its kind of harsh but it worked for me.

[My Original Menus post](http://ubuntuforums.org/showthread.php?t=41213)[/QUOTE]

Hey Omnios... there's no config file on my home/user folder.... Is it possible to be on another location?

---

### Post by Omnios on 2005-07-15
$HOME/..yourfiles../config/menus/applications.menu

 Its in a config directory which is /.config the "." makes it a hidden dirrectory so you have to to views in your user file and click shown hidden in the window options. Should be easy going from there.

---

### Post by fnando on 2005-07-15
okay... I can see hidden files/folders... but there's no .config folder

---

### Post by Omnios on 2005-07-15
It follows this order the files without "." abcd ......etc then the files with "." will start .a,.b,.c....etc. the . start after the non . finish.

 Try this do a file search in home for " applications.menu " From what was explained to me was that this is the local menu config file for you as a user. If removed it should generat a new file with the defaults. Also the file .config will be listed after all the files without a " . "

---

### Post by fnando on 2005-07-15
I did it!

On the bottom bar > Right Click > New Panel
I add the custom menu and some others icons!!!

But thanx a lot!!! \\:D/

---

### Post by Omnios on 2005-07-15
Kewl why didnt I think of that lol.

---

