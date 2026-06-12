---
title: "Avant window navigator - Launchers not getting added"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by ittiam on 2007-08-29
I tried adding launchers (firefox) to the AWN but i dont see it getting added, rather I can see a separator (option is there to have a separator between task list and launchers) between the instance of firefox and other tasks. But i dont just a separate icon for the launchers. Also I adding the workspace switcher applet, it also doesnt get added. But trash icon does get added. Help please.

---

### Post by hibernatus on 2007-08-29
Hi,

I have exactly the same issues, so i'm also interested by the answer 

Hibern

---

### Post by hibernatus on 2007-08-29
Hi ,

I think i have found a solution,

verify in your .config/awn/launchers/
that you have the line Icon in the file corresponding to your laucher  :
> 
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Icon[fr_FR]=/usr/share/pixmaps/mozilla-firefox.png
Exec=firefox
Name[fr_FR]=Firefox
Name=Firefox
Icon=/usr/share/pixmaps/mozilla-firefox.png


regard's
John

---

### Post by ittiam on 2007-08-29
I also figured out a way around it. But even when you open something like firefox from the launcher you dont get a firefox in task list...rather the same icon in launcher is now show as the task icon.

---

### Post by hibernatus on 2007-08-29
Yes that's correct ,

I join a screenshot  where i have 2 windows open 

1 : it's Firefox, their is a launcher in the doc but no icon in the application launch part
2 : it's the home folder, their is also a launcher but when i launch it, a drive icon is show in the launch application part.

it's really stange ...

John

---

### Post by Magneticgravity on 2007-08-29
Do you want to put launchers in your Dock which will stay there when you start up Ubuntu?

---

### Post by notwen on 2007-08-29
Try navigating in Nautilus down to usr/share/apps and once there simply drag each application you're wanting a launcher for to AWN.  Save your session, reboot and check to see if they're still there.

---

### Post by pandan on 2008-02-20
I use Xubuntu. So here's what I did.

Open a terminal and issue command:

slocate *.desktop

This should list all locations of the desktop files (Scroll around it).

Then open a file browser (in my case 'Thunar') and drag
the appropriate .desktop files to the opened AWN dock.

BTW.  xfce's desktop compositing was enough to run AWN (Compiz or derivatives are NOT installed)
There is a general focus issue if you have low specs.  Newer XFCE 4.4.2 to be released in Hardy does fix this (in Hardy beta it works).

---

