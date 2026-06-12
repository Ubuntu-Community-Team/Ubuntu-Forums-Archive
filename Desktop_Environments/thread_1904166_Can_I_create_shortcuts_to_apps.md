---
title: "Can I create shortcuts to apps?"
date: 2012-01-04
forum: Desktop Environments
---

### Post by Aqil on 2012-01-04
Hello!

I am a new Ubuntu user. I just installed Ubuntu 11.10 a couple of days ago to replace Windows 7 on my new computer and I am generally pleased.

Now my dock on the left edge of the screen is getting full of useful applications. So I tried to solve this by placing a folder in the dock and the shortcuts in the folder. Ubuntu won't allow me to do either.

Obviously the applications are easily available by search in the "Dash home" but that requires me to remember the name of my (perhaps rarely used) applications. For example, I installed a flashcard software called Granula and a touch typing tutor called Klavaro. I would like to put shortcuts to these applications in a folder called *"Learning Tolls"*, the three LibreOffice applications in a folder called *"LibreOffice"*, games in a folder called *"Games"* and so on. Otherwise I will quickly forget that my flashcard software is called Granula and that I even have minesweeper to play with when I'm bored.

How do I solve this problem in an easy and intuitive way?

---

### Post by stinkeye on 2012-01-04
You can create your own launchers by making a .desktop file.
To see what a .desktop file looks like open the file browser and press ctrl+h to show hidden files.
Then open the folder **.local/share/applications**
You can't open the .desktop file by clicking.
Open up gedit and drag and drop one of the .desktop files into it.
This will give you an idea of what a .desktop file looks like.
After creating a .desktop file you can then drag it to the launcher.
Do a search for how to create a .desktop file.

Personally I wouldn't bother because one of the benefits of the Dash search is you don't need to remember the name of the app.
eg...if I wanted to launch **Klavaro** but couldn't remember the name,
simply entering in the Dash search "typing" or "tutor" or "touch" will bring up Klavaro.

---

### Post by Aqil on 2012-01-04
Seems complicated to create shortcuts, so for now I'll simply list my applications in a document on the desktop so that I can search for it in the dash.

Isn't there any way to see all the applications installed on my computer? I can't find any such function.

Thank you for your help!

---

### Post by stinkeye on 2012-01-04
See attached pic for how to see all installed apps.

You could create a folder with launchers in it and then place that folder on the desktop.
eg: You can create a folder called "Learning Tools" then open the dash and drag and drop the three office applications into it.
Right click on each of the 3 .desktop files 
**properties > permissions** and tick the execute box.
Then drag the "Learning Tools" folder to the desktop.

---

### Post by Aqil on 2012-01-04
Hmm, I'll play around with it. Thanks!

---

