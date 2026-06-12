---
title: "Cedega Game Shortcuts?"
date: 2005-11-11
forum: Gaming &amp; Leisure
---

### Post by Stambo00 on 2005-11-11
How can I create Cedega game shortcuts so i can add them to my dock?

---

### Post by cydizen on 2005-11-11
Check this out...

[http://transgaming.org/forum/viewtopic.php?t=3330&highlight=shortcuts](http://transgaming.org/forum/viewtopic.php?t=3330&highlight=shortcuts)


This script hooked me up, should do the same for you! Let me know if the link doesn't work...


Regards,
Bruce

---

### Post by Stambo00 on 2005-11-11
It looks promising, but I am unsure on how to run it or install it. Any help?

---

### Post by cydizen on 2005-11-11
Sure Can!  Here we go....

1. Download the file game_launchers.sh

2. Open a terminal and navigate to the folder where you saved this scripts. OR, Navigate there using the gui.

3. You need to change the permission of the file... so if you are in a terminal type: 
```
chmod +x game_launchers.sh
```

or if you are in the gui, then right click the file, and go to properties. Then select the permissions tab... once there, place a check mark in the executable box (for owner)

4. Now, if you are using a terminal, simple type ```
sh game_launchers.sh
```   OR   if you are using the gui, just double click the file and a dialog box will open, just click 'run'.  

5.  Now, either way you went... open your gui and in your home folder you should see a folder called p2pgamelaunchers (or something like that)... open it, you will see a folder for your game... open that, there you should see the icon for the game. 

6. Double click the icon and see if it works!  Once you know it works, feel free to click-n-drag it anywhere you want it!

Hope this helps,
Bruce

---

### Post by Stambo00 on 2005-11-12
I did what your recommended, but my p2pgamelaunchers folder is just full of more folders of my games such as sim city 3000 but are empty without any icons or files of any kind? What could i be doing wrong?

---

### Post by chronusdark on 2005-11-12
what i always do is make a launcher like this

```
[Desktop Entry]
Name=World of Warcraft
Encoding=UTF-8
Exec=/home/lhanners/scripts/wow.sh
Terminal=false
Type=Application
Name[en_US]=World of Warcraft
Icon=/home/lhanners/Documents/Icons/WowIcon12.png
```

and the wow.sh looks like this

```

cedega "/home/lhanners/Transgaming_Drive/Program Files/World of Warcraft/wow.exe"
```

and dont forget to 
```
chmod +x wow.sh
```

doing that makes a nice icon that looks like the attachment

you can get some really nice PNG icons from [www.deviantart.com](www.deviantart.com)

---

