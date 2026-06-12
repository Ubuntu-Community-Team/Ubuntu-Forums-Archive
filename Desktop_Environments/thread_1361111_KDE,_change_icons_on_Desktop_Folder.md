---
title: "KDE, change icons on Desktop Folder"
date: 2009-12-21
forum: Desktop Environments
---

### Post by VMC on 2009-12-21
I'm fairly new to KDE4 and have googled without success.

How do I change icons on Desktop Folder?(That is the square box that is at the upper left of my Desktop.)

 I have several shortcuts I want to change to match what they are. 

I thought I was able to change, but what I ended up changing was the icon for the programs themselves.

I have attached the Desktop Folder in question.

---

### Post by garryknight on 2009-12-21
Right-click the icon, click Properties, then click the icon to the left of the name. Then look through the lists of available icons until you find the one you want.

---

### Post by VMC on 2009-12-21
> **garryknight said:**
> Right-click the icon, click Properties, then click the icon to the left of the name. Then look through the lists of available icons until you find the one you want.

Thanks for the replay, but apparently KDE doesn't work that way. Gnome works fine doing that.

---

### Post by Zorael on 2009-12-21
How did you create those links?

If you pick Link to Application from the right-click context menu, and then point it to the app you want, it creates a .desktop file from scratch and you can change the icon freely.

---

### Post by VMC on 2009-12-22
> **Zorael said:**
> How did you create those links?

If you pick Link to Application from the right-click context menu, and then point it to the app you want, it creates a .desktop file from scratch and you can change the icon freely.

Thanks for reply. Here's what I found out. Google-chrome had a file that I linked to. I could also right-click and change icon. I also found konsole that I could right-click and change. It was found at "/usr/share/applications/kde4/konsole.desktop". Any executable found at "/usb/bin" or any other bin would not allow right-click change icons. I'm still trying to find one for xterm.


Strange, as with Ubuntu Gnome , I can almost always just right-click anything that I created a link to.

===
Edit:BTW, I like your signature, "Try a Kubuntu live cd before you dismiss it.". I did dismiss it with all the FUD about Kubuntu going around. Was I in for a suprise. Great distro.
I also do a save as shortcut.

---

### Post by Zorael on 2009-12-22
I can't reproduce this. Perhaps I'm misinterpreting what you mean when you say that Chrome had a file that you "linked to".

I copied Dolphin's .desktop file (**/usr/share/applications/kde4/dolphin.desktop**) to my desktop directory, and then right-clicked it in my folder view widget and changed its name and icon. Even after having run **kbuildsycoca4** (which parses .desktop files to enumerate the menu and register mime-types), the menu entry for Dolphin still has the standard values.

If you make a *symbolic link* to said .desktop file, that's another matter. You normally shouldn't have the privileges to modify it then (to change its icon), unless you have set yourself up to be root, as it is still technically a file located outside of **/home/*username***. That .desktop file is the application's own file, containing information about it. That includes its name, description, comment, icon, and other options like whether it should be shown in GNOME/KDE, whether it should give startup notifications, what files (mime-types) it can open, etc.

The files in **/usr/bin** are the executables, which cannot as such have icons. As mentioned, what icon an application should have is instead defined in its .desktop file.

---

### Post by VMC on 2009-12-23
I don't even know enough about KDE4 to answer your question. Using Ubuntu Gnome, if I drag an executable from, say "/usr/bin/xterm" to my panel, It automatically creates a launcher and then I can change its icon. 

I tried that using Kubuntu and it asked three things, Move,Copy or shortcut. No matter what I choose I can't change its icon. I'm moving from "/usr/bin/xterm" to my desktop "Desktop Folder".

---

### Post by benerivo on 2009-12-23
In kde it would be best to right click inside your 'Desktop Folder' and select 'Create New' > 'Link to Application'. From there you can go to the 'Application' tab to enter your own name for the link, and browse for the application in the 'Command' field. You can set the icon by clicking on the question mark icon in the 'General' tab.

There are also other ways to make shortcuts and links to apps.

---

### Post by VMC on 2009-12-24
> **benerivo said:**
> In kde it would be best to right click inside your 'Desktop Folder' and select 'Create New' > 'Link to Application'. From there you can go to the 'Application' tab to enter your own name for the link, and browse for the application in the 'Command' field. You can set the icon by clicking on the question mark icon in the 'General' tab.

There are also other ways to make shortcuts and links to apps.
Thanks. That did it! The key was the Link to applications. I have know idea how I missed it. I think once I go caught up on linking directly to an executable, I worked it on that angle.

---

