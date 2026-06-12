---
title: "Need help with game startup commands"
date: 2009-02-26
forum: General Help
---

### Post by jnewl on 2009-02-26
(Sorry for the double post. I originally posted this to the Wine forum, but no one responded. I figure I'll have more luck here, since in the end it's not really a Wine question.)

When I install a Windows game to be played under Wine, my normal procedure is to run the install and tell InstallShield to put an icon on my desktop. Then, after running and tweaking the game as necessary, I create a menu item under Applications -> Games using System -> Preferences -> Sessions. The command line I put in the menu item is then copied and pasted from the desktop icon's Properties dialog. The thing is: sometimes this works and sometimes it doesn't. Sometimes the menu entry fails to start the game, although the desktop icon works fine, or it starts the game, but with issues.

So my question is, when this doesn't work, what do I need to do to make it work? I'm assuming the game isn't finding needed files for some reason when launched from the menu, but I don't know what I need to add to the command line (or elsewhere) to tell it where to look.

P.S. Obviously, I'm trying to keep games icons off my desktop. Otherwise, I'd just run them from there. I also don't want to use the terminal unless I absolutely have to.

---

### Post by mc4man on 2009-02-26
May not help but try shortening the command you're using in the menu.
I'd assume your using something like this

 env WINEPREFIX="/home/doug/.wine" wine "C:\Program Files\ImgBurn\ImgBurn.exe"

see if cutting down like this works any better

wine "C:\Program Files\ImgBurn\ImgBurn.exe"

or double backslash

wine "C:\\Program Files\\ImgBurn\\ImgBurn.exe"

(there is a way to launch program exe's with just the program name the same as notepad and regedit work. I use it for 2 things though maybe not suitable for games.

---

### Post by jnewl on 2009-02-26
Nope. No go on either count. Let me describe what happens with this one game in particular:

When I launch from the *desktop icon*, it opens in a 1280x1024 window--which is what I have it configured to do in winecfg--and then runs normally. The loading screen at startup is black, with a progression bar at the bottom and a graphic above it.

When I launch from the *menu entry*, it opens in a 1280x1024 window, but then immediately switches to an 800x600 window (which, maybe coincidentally, is the default resolution of the game, though that's not what I have it set to in the game's Options). In this window I can see the progression bar, but there's no graphic. Once the bar is filled, the screen goes completely black. At this point, it may be going through the proper motions or not, I can't tell. But clicking all over the screen yields no reaction, so I eventually have to close it with the X button.

Weird, no?

When I install stuff and it puts an icon on the desktop, it also places a file that ends in .lnk there. Should I be doing something with that file? I normally just trash it.

---

### Post by mc4man on 2009-02-26
It is wierd, don't have any games installed to fool with, though something must be different in the case you've mentioned.

Why not try just using the path to the .exe, so for example with my ImgBurn.exe (note not using wine at all in the command

> /home/doug/.wine/dosdevices/c:'/Program Files/ImgBurn/ImgBurn.exe'


Your 'icon' is really a .desktop, open it up in gedit and see if anything is different about the path.
To do that (using ImgBurn icon as ex.

> gedit ~/Desktop/ImgBurn.desktop
> 
it also places a file that ends in .lnk there

I don't believe there's any reason to keep them, they're the windows 'link' file

---

### Post by mb_webguy on 2009-02-26
> **jnewl said:**
> When I launch from the *desktop icon*, it opens in a 1280x1024 window--which is what I have it configured to do in winecfg--and then runs normally. The loading screen at startup is black, with a progression bar at the bottom and a graphic above it.

When I launch from the *menu entry*, it opens in a 1280x1024 window, but then immediately switches to an 800x600 window (which, maybe coincidentally, is the default resolution of the game, though that's not what I have it set to in the game's Options). In this window I can see the progression bar, but there's no graphic. Once the bar is filled, the screen goes completely black. At this point, it may be going through the proper motions or not, I can't tell. But clicking all over the screen yields no reaction, so I eventually have to close it with the X button.
Is there a difference in the command used by the desktop launcher and the menu launcher?  Right-click on the desktop icon and go to Properties to see the command it uses.  Now right-click on your menu, select Edit Menus, and find the launcher for the game.  Double-click this to bring up the properties, and check out the command it uses.  If it's a different command, copy and paste the desktop launcher command to the menu launcher.

---

### Post by jnewl on 2009-02-26
Here's what's in the .desktop file:

[INDENT][Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Space Colony
Exec=env WINEPREFIX="/home/jim/.wine" wine "C:\\Program Files\\Firefly Studios\\Space Colony\\Space Colony.exe"
Type=Application
StartupNotify=true
Path=/home/jim/.wine/dosdevices/c:/Program Files/Firefly Studios/Space Colony
Icon=/home/jim/.local/share/icons/ad4c_space colony.0.xpm[/INDENT]

And here's what's in the menu entry's command line:

[INDENT]env WINEPREFIX="/home/jim/.wine" wine "C:\Program Files\Firefly Studios\Space Colony\Space Colony.exe"[/INDENT]

The double slashes make no difference. I added them to the menu entry and it still behaves the same way. I'm sure the solution has something to do with that Path address, but I don't know how to add that to the command line. Do I need some kind of symbolic link put somewhere?

---

### Post by mc4man on 2009-02-26
Maybe try this (assuming you haven't changed anything in the desktop icon

First go to home folder/.local/share/applications and make sure there is no Space Colony .desktop there. if so delete. (in other words get rid of anything created when you've tried adding thru edit menus, plus if you named it Space Colony in edit menus, first rename it and then remove
 
gedit your Space Colony.desktop and add this line underneath the line Type=Application and save

```
Categories=Applications;Game;
```

Then in a terminal go (adjust the .desktop name if I got it wrong (must be exact

```
 cp ~/Desktop'/Space Colony.desktop' ~/.local/share/applications

```

Then look in Applications -> Games and see if it works
(if it doesn't work  you can go to home folder -> .local/share/applications and delete the Space Colony.desktop (shift+delete


Edit: you have to get the copy command to work, I don't believe you can 'physically' move the .desktop and have it recognized.

Also just for info, once a .desktop is created the .desktop's 'real' name can't be changed, only the 'display' name, so because yours has a space you need to get the '...' right

did it with ImgBurn and now it's in my 'Games' menu

---

### Post by jnewl on 2009-02-26
Yes! Works like a charm. Thanks very much :KS :KS :KS :KS :KS

I'm saving this page to my computer until I form the habit of editing those .desktop files :)

---

### Post by mc4man on 2009-02-26
Great..
There's a lot of interesting things you can do with .desktops, the applications folder and mimeapps.list.
Let me know I'll give you some links

Edit: just to clarify something. When I said "physically move" I was referring to 'drag and drop' or 'copy and paste'. In this case because the original .desktop (the desktop icon) is of no value afterwards, the copy command (cp) could be replaced with a move command (mv)

The main point is that this (and related uses of .desktops) need to be done from the command line, not 'physically done' so to speak.

---

