---
title: "Launcher icon defaults when in unity sidebar"
date: 2011-07-15
forum: Desktop Environments
---

### Post by Jalaska13 on 2011-07-15
So I made a launcher for a script that I use frequently, and I gave the launcher an Icon.  However, when I dragged the launcher to the sidebar, the icon defaulted to the little springy platform.  Is it possible that my file setup is the culprit?  I have it like this:
~/.local/share/Launchers/myLauncher
~/.local/share/Launchers/Icons/myIcon.png
Do I have to put the icon somewhere else?  I tried putting them in .local/share/applications and .local/share/icons and that didn't work either.

---

### Post by Steve H on 2011-07-18
I've been trying the same thing for a while now. I've traced most of the unity config folders but I'm yet to find the one responsible.

Really annoying.

---

### Post by Jalaska13 on 2011-07-18
The really weird thing, though, is that it worked with another program that wasn't one of mine.  It also worked with a launcher for another program (also not written by me).  In fact, it even worked for a launcher that pointed to a script that opened a folder.  The script I'm trying here uses python, although I really doubt that has anything to do with it.

---

### Post by Steve H on 2011-07-18
I just created a desktop link then dragged it to the sidebar. Great! I thought and promptly deleted the desktop link and that was when the icon defaulted. To me it defeats the object if you have to have both a desktop link and a sidebar link for it to work.

---

### Post by Jalaska13 on 2011-07-18
What I do is keep a "Launchers" folder (I put mine in ~/.local/share/).  I'm not in Ubuntu at the moment, but when I go back I'll try adding it from the desktop and seeing if that works.

---

### Post by Pirate Zoro on 2011-07-18
Add the launcher to ~/.local/share/applications, then add it to the dock from there. I did this with a command to manually activate the screensaver when I was using Unity, and the icon should remain constant

---

### Post by Jalaska13 on 2011-07-18
I tried that and it didn't work.  Where did you put the logo that the launcher used as its icon?

---

### Post by Pirate Zoro on 2011-07-18
I made the launcher on the desktop so that I could add the icon to the launcher itself, then put that in the application folder. That way when I put it in the dock it had the icon

---

### Post by Jalaska13 on 2011-07-18
Wait, when you say add the icon to the launcher itself, what do you mean?  The way I do it is open the preferences for the launcher, click on the icon (which brings you to a file select dialogue) and select the image file.  Is that what you mean?  And then drag the launcher to the dock?  Cuz that's exactly what I did, just not on the desktop (made the launcher on the desktop, then dragged it to a new folder, then added the icon, then dragged to dock).

---

### Post by mc4man on 2011-07-18
Maybe post the contents of your launcher(XXXX.desktop

.desktops won't open in directly in a text editor (I use nautilus-actions to create an option), just open gedit >  then drag & drop your launcher into the gedit window.
Small possibility there may be something 'wrong' in it.

---

### Post by Jalaska13 on 2011-07-19
GOT IT TO WORK.  ...have no idea why.  Here's what I did (not sure which steps are the key ones, though):
Created launcher on the desktop and selected the icon while the launcher was still on the desktop.  Dragged to sidebar.  Moved the launcher to ~/.local/share/applications.  The icon disappeared from the sidebar when this happened.  Then I dragged it to the sidebar from the applications folder and it worked.

---

### Post by mc4man on 2011-07-19
> **Jalaska13 said:**
> GOT IT TO WORK.  ...have no idea why.  not sure which steps are the key ones, though):


Created launcher on the desktop and selected the icon while the launcher was still on the desktop.
Moved the launcher to ~/.local/share/applications. 
dragged it to the sidebar from the applications folder

---

### Post by Jalaska13 on 2011-07-19
> **mc4man said:**
> Created launcher on the desktop and selected the icon while the launcher was still on the desktop.
Moved the launcher to ~/.local/share/applications. 
dragged it to the sidebar from the applications folder

Do you happen to know why that step in particular?  And why did it work when I removed it from the sidebar, moved the launcher to applications folder, and added it back?

---

### Post by chrisgerow on 2011-11-11
Im having trouble placing the launcher in the application folder.  No permission. Folder belongs to root?  This maybe a newbie question but how do I place the launcher in the root owned folder?

I'm using a launcher just to launch separate firefox profiles.

---

### Post by stinkeye on 2011-11-11
The folder should not belong to root.
Are you sure your opening the right folder?
In the terminal
```
nautilus ~/.local/share/applications
```

---

### Post by clockworkpc on 2012-08-26
Hey guys, maybe this will help someone.

I'm on Ubuntu 12.04:

I created an desktop icon to launch a game via Dosbox (Heroes of Might and Magic if anyone is interested) and found that even though the custom icon appeared in Nautilus, it didn't carry over to the dock:

Long story short, the problem lay in the .desktop file, which had two Icon entries:

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
[COLOR=Red]Icon[en_AU]=gnome-panel-launcher[/COLOR]
Name[en_AU]=Heroes of Might and Magic
Exec=/bin/bash homm1.sh
Name=Heroes of Might and Magic
[COLOR=Red]Icon=/usr/share/icons/homm.png[/COLOR]
```All you have to do is comment out the one you don't want or just delete it:

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
[COLOR=Blue]#Icon[en_AU]=gnome-panel-launcher[/COLOR]
Name[en_AU]=Heroes of Might and Magic
Exec=/bin/bash homm1.sh
Name=Heroes of Might and Magic
Icon=/usr/share/icons/homm.png
```Hope this helps.

---

