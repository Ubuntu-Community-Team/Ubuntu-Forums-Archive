---
title: "is there any way i can open two window manager?"
date: 2023-07-04
forum: Desktop Environments
---

### Post by tojonukokhadush on 2023-07-04
can i open two window managers at the same time? new tab is not helping me for my purpose.

---

### Post by SeijiSensei on 2023-07-04
Sure. You can have as many instances as you like. Did you try just launching it a second time?

---

### Post by tojonukokhadush on 2023-07-05
not by GUI though.

---

### Post by tojonukokhadush on 2023-07-05
no. its not working on my ubuntu 22.04. please help.

---

### Post by SeijiSensei on 2023-07-05
I misread your question. I thought you were asking about file managers. For window managers, a quick Google search brings up the i3 application: [https://forum.endeavouros.com/t/how-to-try-out-multiple-window-managers/22541](https://forum.endeavouros.com/t/how-to-try-out-multiple-window-managers/22541). It's in the Ubuntu repositories.

---

### Post by Holger_Gehrke on 2023-07-05
Do you actually mean a **window **manager ? As in: the part of the GUI stack that allows the user to move and resize windows and draws the window decorations (title bar, borders and the buttons on the titlebar) and reacts to clicks on the 'close', 'maximize', and 'minimize' buttons or something else ? I'm asking because I don't know any wm that has tabs or the ability to open new tabs ... 
It is possible to have multiple window managers if you're using something like Xnest (an X-Server inside a window on another X-Server) but it is rather unusual.

Holger

---

### Post by tojonukokhadush on 2023-07-06
yes exactly, i meant that. or actually this will help me- two tabs that could be screen-split into two so that i can work on two simultaneously. thank you.

---

### Post by ajgreeny on 2023-07-06
Can you give us an exact example of what you want to do as I don't quite follow you at the moment, and like Holker, I don't think it's possible to run two window managers simultaneously in a session; it has to be one or the other at any one moment, not both together.

It almost sounds as if you need two instances of, for example, firefox running in separate windows side by side which is certainly possible if you resize and place each window appropriately, using any window manager I believe..

---

### Post by tojonukokhadush on 2023-07-06
it would make me work on two folders at a time like while dragging files. the concept of tab is okay but there is no clear demarcation of the two screen and you constantly keep messing things around.

---

### Post by tea for one on 2023-07-06
> **tojonukokhadush said:**
> it would make me work on two folders at a time like while dragging files. the concept of tab is okay but there is no clear demarcation of the two screen and you constantly keep messing things around.
Are you referring to the File Manager application i.e. nautilus (Files)?
You can open the application twice and tile the windows side by side.

---

### Post by DuckHook on 2023-07-06
We are all getting needlessly tripped up by improper terminology here.

@tojonukokhadush

A Window Manager is the underlying graphics engine that makes your desktop run. It is not what you are thinking and definitely not what you are actually asking for.

If you are looking for the two&#8209;pane experience that allows you to drag files from one side to another, then I suggest the following:

[LIST=1]
[*]For the "original" experience, open up a terminal and use Midnight Commander:```
sudo apt install mc
```
[*]For a GUI version of the Midnight Commander experience, use Krusader: ```
sudo apt install krusader
```
[*]Another GUI option is Double Commander: ```
sudo apt install doublecmd-gtk
``` or ```
sudo apt install doublecmd-qt
``` (depending on whether your real ***Window Manager*** is based on GTK or QT)
[/LIST]
I've used Midnight Commander for decades and it's always my go to for more complicated file manipulations. I've never felt the need to go fully GUI for two panes and will fire up a terminal session to use MC which is faster and more intuitive.

---

### Post by tojonukokhadush on 2023-07-07
> **tea for one said:**
> Are you referring to the File Manager application i.e. nautilus (Files)?
You can open the application twice and tile the windows side by side.


no way. i wouldn't be asking this else. thank you though.

---

### Post by tojonukokhadush on 2023-07-07
> **DuckHook said:**
> We are all getting needlessly tripped up by improper terminology here.

@tojonukokhadush

A Window Manager is the underlying graphics engine that makes your desktop run. It is not what you are thinking and definitely not what you are actually asking for.

If you are looking for the two&#8209;pane experience that allows you to drag files from one side to another, then I suggest the following:

[LIST=1]
[*]For the "original" experience, open up a terminal and use Midnight Commander:```
sudo apt install mc
```
[*]For a GUI version of the Midnight Commander experience, use Krusader: ```
sudo apt install krusader
```
[*]Another GUI option is Double Commander: ```
sudo apt install doublecmd-gtk
``` or ```
sudo apt install doublecmd-qt
``` (depending on whether your real ***Window Manager*** is based on GTK or QT)
[/LIST]
I've used Midnight Commander for decades and it's always my go to for more complicated file manipulations. I've never felt the need to go fully GUI for two panes and will fire up a terminal session to use MC which is faster and more intuitive.



yes exactly. i was expecting in full GUI though; is there such an app? thank you.

---

### Post by DuckHook on 2023-07-07
> **tojonukokhadush said:**
> …i was expecting in full GUI though; is there such an app? thank you.
Okay, so you were, in fact, looking for a system&#8209;level solution.

The easiest and least troublesome way is to not change anything at the system level, but just download Krusader or DoubleCMD and just open them in maximized mode. This only requires one click (or shortcut key).

If you want to go full Die Hard on it, then do as SeijiSensei suggests and change your Window Manager to i3wm or Awesome or any similar WM that opens everything up in tiled mode. See the link in my sig for explanation and options: [https://ubuntuforums.org/showthread.php?t=2415676](https://ubuntuforums.org/showthread.php?t=2415676)

I don't understand why you would do that though. It's very much like trying to swat a fly with a blunderbuss.

---

### Post by tojonukokhadush on 2023-07-10
i found it. shift + file_manager_icon will open as many instances as i need. thank you everyone for the help.

---

