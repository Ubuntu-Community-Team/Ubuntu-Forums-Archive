---
title: "Attal, request for help"
date: 2009-08-09
forum: Gaming &amp; Leisure
---

### Post by mringer on 2009-08-09
Ubuntu 8.04:
I tried to install Attal . The install ran with no visible error
but I cannot find how to start the game. There is no entry for Attal in 
the games menu. Please any advice? thank you.

---

### Post by zarthon on 2009-08-09
In Gnome you can run any program by typing alt-F2
then Typing the name of the executable which in many cases will match the name of the program. 
The dialog that appears will provide some auto completion but the keystrokes to choose and accept these results are not what i expect so i often just type the whole thing or just click the choice I want.:popcorn:

Additionally you can run graphic programs from the command line. To keep your command prompt run these programs in the background by ending the line with &
so you may be able to run the program by typing
```
executable-file-name &

```
at a command prompt.

---

### Post by zarthon on 2009-08-09
I installed it and found that it is a fairly complex client / server program

To get a list related programs at a command prompt type
attal- [tab][tab]

It seems you must run the server and then then client and then load a game and start it, or run the client and find a server to connect to.

At the point where I needed to load a game I got fairly stuck. It is most likely under /usr/share/
:confused:

The package does not update the locate database. You will need to update it to find where game files might be stored
```

sudo updatedb
locate attal

```

I could find no obvious options with a quick glance through the list. 
Go to the website for the game to figure out where to go from this point.

A Bug might be entered on launchpad against this package for not integrating with the Gnome Menu.

Other problems such as errors and segmentation faults should be reported to the authors of the program not the Ubuntu package.

Maybe someone that plays this game will chime in with how to proceed.

---

### Post by zarthon on 2009-08-09
I figured it out.
in Gnome type alt-F2 and in the box type 
attal-client
in attal-client go to the File menu and select "Fast Server..."
In the dialog that appears click "Start"
and a basic game will start.

Thank you for the serendipitous intro to the game. I think I will try it out.

---

### Post by Crunchy the Headcrab on 2009-08-09
You can add programs to the main menu through system > preferences > main menu
or  by typing alacarte in the terminal.  ;)

---

