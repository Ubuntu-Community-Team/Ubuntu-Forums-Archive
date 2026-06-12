---
title: "Add shortcuts to unity launcher?"
date: 2012-05-03
forum: Desktop Environments
---

### Post by c-m on 2012-05-03
How do I add program shortcuts to unity launcher in ubuntu 12.04?

I have chromium installed that I want on the launcher. If i drag it to the launcher then I don't get an icon.

Same for XBMC and every other program i've tried.

---

### Post by thunk77 on 2012-05-03
Just start the app. When started you'll see its icon on the launcher. Right click on icon, click on "Lock to Launcher", done!

---

### Post by c-m on 2012-05-03
> **thunk77 said:**
> Just start the app. When started you'll see its icon on the launcher. Right click on icon, click on "Lock to Launcher", done!


Again it just added a blank space with no icon.

Then when i removed it, it never showed the app again even when it was running.

---

### Post by 2ta8gdfte on 2012-05-03
> **c-m said:**
> Again it just added a blank space with no icon.

Then when i removed it, it never showed the app again even when it was running.

 Does the dash show normal, I have seen others use and and had to use a unity reset to reset it myself to the install unity. Try alt-f2 unity --reset

---

### Post by c-m on 2012-05-03
I reset the computer and now the panel is populated correctly.

Also now when I drag something there it sticks.

No idea what caused the issue mind.

---

### Post by 2ta8gdfte on 2012-05-03
> **c-m said:**
> I reset the computer and now the panel is populated correctly.

Also now when I drag something there it sticks.

No idea what caused the issue mind.

I have had to reset unity a few times did on a fresh install of precise just now in a virtualbox. there is also unity --replace which restarts it as well.

---

### Post by deonis on 2012-05-03
create a text file "programname.desktop" somewhere with the following instructions, of course use the correct path to your program: 

[Desktop Entry]
Name=Linxtl
Comment=Crystallographic toolbox for Linux
Exec=/home/denis/.linxtl/linxtl.py
TryExec=/home/denis/.linxtl/linxtl.py
Icon=/home/denis/.linxtl/icon/main.ico
StartupNotify=false
Terminal=false
Type=Application
Categories=Science; Chemistry

and then in terminal run: xdg-desktop-menu install --novendor /path/to/programname.desktop

---

### Post by gpeck157 on 2012-10-02
> **thunk77 said:**
> Just start the app. When started you'll see its icon on the launcher. Right click on icon, click on "Lock to Launcher", done!Your solution worked for me. Thanks!

---

### Post by webdesigncompanyla on 2013-03-28
i would like to just be able to drag a text file that i use EVERY DAY to the bar instead of having to create a file to launch a file (how stupid)  this is the reason i ditch unity and install gnome 3 and docky... unity is just a little baby and kind of sucks

---

### Post by webdesigncompanyla on 2013-03-28
i'm trying this http: //www.noobslab.com/2013/01/mechanig-unity-customization-tool-for.html

---

### Post by stinkeye on 2013-03-28
> **webdesigncompanyla said:**
> i'm trying this http: //www.noobslab.com/2013/01/mechanig-unity-customization-tool-for.html

You may find the [**_[COLOR="#B22222"]Drawers[/COLOR]_**]("http://www.webupd8.org/2013/03/get-classic-style-menu-in-unity-with.html") useful.

Can drag and drop favourite folders or files into it.

---

