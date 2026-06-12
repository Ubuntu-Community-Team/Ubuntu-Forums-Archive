---
title: "Joy and Vexation of Adding a Launcher in Unity"
date: 2016-10-04
forum: Desktop Environments
---

### Post by Kleenux on 2016-10-04
[COLOR="#B22222"][SIZE=2]Using Ubuntu 16.04.1 regular Desktop (Unity)[/SIZE][/COLOR]

Somehow adding a Launcher icon in **14.04** was **awkward**, but it usually worked.

In **16.04**, copying the icons from **14.04** (~/.local/share/applications/*) didn't work. For some reasons.
Using `desktop-file-validate` helped me to fix / remove the undesired/wrong tags (...) and after many hours of try and hard work I could get most of them working.
[ Of course I didn't rely on Gnome being able to detect icons/desktop files changes (because it's unreliable), and logged out / back in all the time ]

Seemingly Gnome and its launcher require an intelligence way higher than mine, so maybe someone can offer some clarification:


**1) Icons forking**

Clicking on some icons just opens the application (eg Gimp), but other icons fork, I mean another same icon appears below in the launcher for the active application (eg my custom apps...), the original icon is not "active".
What triggers this behavior? 
How to have an icon *not* fork?


**2) What is the real/reliable/recommended way to refresh the launcher after a change?**

After a change (in ~/.local/share/applications/(x).desktop) an indicator window says that there were some changes (actually it says erroneously "Software Updates available").
But often the change is not visible in the launcher.
Do I need to log out/in each time?

Thanks!

---

### Post by CantankRus on 2016-10-04
Do you have an example of a .desktop file that launches a new icon.
I have a number of custom launchers I have copied through different releases without problem.

You can just run "unity" in terminal to reload panel and launcher or unlock and re-add an individual launcher after editing.

---

### Post by Kleenux on 2016-10-06
This is one desktop file that launches a new icon

[FONT=Courier New][Desktop Entry]
Name=XTerminal
Comment=Use the command line
TryExec=/home/me/bin/metm
Exec=/home/me/bin/metm
Icon=utilities-terminal
Type=Application
Categories=GNOME;GTK;Utility;TerminalEmulator;
Keywords=Run;
Actions=New;Zebu;

[Desktop Action New]
Name=New Terminal
Exec=/home/me/bin/metm

[Desktop Action Zebu]
Name=Super Terminal
Exec=/home/me/bin/metm -e "/home/me/bin/xterminal"
[/FONT]

This is a special terminal - the exe 'metm' is a special binary made by me.

---

### Post by CantankRus on 2016-10-06
Your desktop file appears ok and seems to work here in Xenial.
Strange thing here is I'm seeing what you describe in Yakkety.
If I drag the terminal from dash to the launcher, when the launcher icon is clicked it spawns a new terminal icon.
But if I launch a terminal by clicking in the dash then lock the resultant icon to the launcher, it works as should. :confused:

---

### Post by Kleenux on 2016-10-07
Maybe we could understand what's happening if a manual somewhere describes in details what makes an icon "spawn"..

---

