---
title: "Help with Launchers!!"
date: 2012-05-29
forum: Desktop Environments
---

### Post by garyzw on 2012-05-29
How do I get my launchers(shortcuts) to show up under the proper filter in Unity Dash. In the picture I have some game launchers I would like to show up under games-- but how?

---

### Post by mc4man on 2012-05-29
Open your launcher,  (<whatever>.desktop),  in a text editor & add this line
 ```
Categories=GNOME;GTK;Game;
```
Then maybe a log out in

If still no go copy & paste the contents of launcher in a reply here

---

### Post by garyzw on 2012-05-29
I added the line but no go--this is the contents of launcher

> [Desktop Entry]
Name=Caesar 3
Exec=env WINEPREFIX="/home/gary/.wine" wine C:\\\\windows\\\\command\\\\start.exe /Unix /home/gary/.wine/dosdevices/c:/users/Public/Start\\ Menu/Programs/GOG.com/Caesar\\ 3/Caesar\\ 3.lnk
Type=Application
StartupNotify=true
Path=/home/gary/.wine/dosdevices/c:/Program Files/GOG.com/Caesar 3/
Icon=1F02_gfw_high.0
Categories=GNOME;GTK;Game;

The file is in the /home/user/desktop-directories


> **mc4man said:**
> Open your launcher,  (<whatever>.desktop),  in a text editor & add this line
 ```
Categories=GNOME;GTK;Game;
```
Then maybe a log out in

If still no go copy & paste the contents of launcher in a reply here

---

### Post by mc4man on 2012-05-29
Wine can be a bit different - atm I don't have wine installed (on 12.10

2 things - 
usually with wine I use different Exec=, you are using a wine created one, may or may not matter here

The .desktop should  be moved to ~/.local/share/applications (.local is a hidden file in your home folder

Try moving it there, log out/in & see. 
===============================================================
If not maybe we could create a new .desktop that would behave better
If that becomes the way to go need the actual path to  the .exe with exact .exe name

Path appears to be this, fill in red
/home/gary/.wine/dosdevices/c:/Program Files/GOG.com/Caesar 3/[COLOR="Red"]Something.exe[/COLOR]

---

### Post by garyzw on 2012-05-29
Moving the file to ~/.local/share/applications worked--thanks a bunch! :D

---

### Post by mc4man on 2012-05-29
Curious - 
when you launch your wine game - does it show in the launcher as it's own icon or does it show in a wine icon (wine glass

---

### Post by garyzw on 2012-05-29
Some games it shows the wine icon--sometime the game icon on others-- if it shows the wine icon I change it in the properties.

Adding Categories=GNOME;GTK;Game; seems to only work with some of them-- I am trying to figure out why?


> **mc4man said:**
> Curious - 
when you launch your wine game - does it show in the launcher as it's own icon or does it show in a wine icon (wine glass

---

### Post by garyzw on 2012-05-29
Thanks mc4man, your tips solved my problem. I got all my games to show up. Ubuntu should have an easier way to do this though. Some sort of menu editor would be a great help.

---

