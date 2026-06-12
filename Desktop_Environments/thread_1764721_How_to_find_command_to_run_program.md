---
title: "How to find command to run program?"
date: 2011-05-22
forum: Desktop Environments
---

### Post by Flame_Phoenix on 2011-05-22
Hello guys, I am trying to add an application to the start up menu by following this tutorial:
[https://help.ubuntu.com/community/AddingProgramToSessionStartup](https://help.ubuntu.com/community/AddingProgramToSessionStartup)

However, in order to do so, I need to know which command runs the application, but I can't find it. Is there a way to know this using the cumbersome Unity?

Thanks in advance.

---

### Post by Frogs Hair on 2011-05-22
The command includes a path to the program location . When use the add option in startup applications you will see the browse button , use that to locate the program or enter the path manually.

If you select a program already on your startup list you will see an example of a command and what it includes.

---

### Post by Copper Bezel on 2011-05-22
Yeah, navigate to /usr/share/applications and load the application's launcher in gedit. There will be a line beginning Exec=, followed by the command sent. Often it'll be the whole path to the binary, but you usually only need the name of the executable, since it's in your PATH, so /usr/games/sol can be run as just sol.

It's usually easier to guess. The majority of the time, it's the application's package name.

---

### Post by Larkspur on 2011-05-22
Another way would be to open Main Menu, go to the program listed in there and click properties.  This will bring up a dialogue showing the command to launch it.  It's like Copper Bezel's solution, but doesn't involve opening .desktop files.

---

### Post by Copper Bezel on 2011-05-22
Good point. It didn't occur to me to use Alacarte (since Unity doesn't use it directly) but it's still going to be in the Dash and fully configured, since Unity itself depends on its entries.

---

### Post by Flame_Phoenix on 2011-05-23
Going to menu? That's kinda ... impossible with Unity because there really isn't a menu ... and right-clicking anything inside the search applications function that Unity offers simply doesn't work ... God ... I wonder how it is possible for Gnome to be the official Interface in one edition and a renegade with no support in the other ... I wonder if I should swap to Gnome3 for good and get rid of Unity.

Anyway, I fixed the problem messing up with .desktop files. Thanks for the help guys. Case solved :D

---

