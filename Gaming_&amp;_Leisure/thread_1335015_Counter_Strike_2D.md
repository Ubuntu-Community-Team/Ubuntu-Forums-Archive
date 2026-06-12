---
title: "Counter Strike 2D"
date: 2009-11-23
forum: Gaming &amp; Leisure
---

### Post by The_Weaver on 2009-11-23
Tried Installing Counter Strike 2D by unpacking both the win zip and the linux files (and copying them into the same folder). I've checked in Synaptic and libstdc++5 is marked as installed (as is libstdc++6). But not sure how to run it ? I've tried double clicking on  the files (Counterstrike2D, Launcher.sh, launcher.exe, Counterstrike2D.exe) to run them (I also changed the permissions to allow executing file) , but nothing happens. Any ideas ? Thanks.

---

### Post by Janneman27 on 2009-11-23
Are you using WINE?

Ubuntu doesn't make use of executable (.exe) files as in Windows, so they won't work unless you install the prgram under WINE.

---

### Post by The_Weaver on 2009-11-23
I've installed the Linux package & couldn't get it to work, so tried the .exe out of desperation.

---

### Post by The_Weaver on 2009-11-24
Should have mentioned I have a Acer Aspire one 1GB ram, running 9.04

---

### Post by 5nak3 on 2009-12-02
I think the problem is that Counter Strike 2D tries to run in 32bit colour mode, but I'm guessing your PC supports 24bit.

As a result the game will not run. I do not have a solution as I too have fallen into the same trap and while I can change the colour mode I cannot get the launcher to work.

If you want to try and change the colour mode:

Open up terminal

Drag and drop launcher.sh into terminal

Then I belive you have to choose option 3 (colour mode) -> Option 2 (24bit)

Then after doing this go back to the main menu, save your new launcher and then try to run the game.

---

### Post by 5nak3 on 2009-12-03
I figured out how to run counter strike 2d on linux and funnily enough it actually runs better than it does on my windows partition...guess there is a first for everything!

Anyways onto the step by step:

**Step one:** Right click on the application menu on the top taskbar and select "edit menus"

**Step two:** Click on the "Games" option

*[COLOR="red"]If you want to organise your games via submenus e.g Action, Adventure, Puzzle, Strategy etc...click on the correct submenu for your classification of Counter Strike 2D[/COLOR]*

**Step three:** Select "New Item" from the right hand side of the window

**Step four:** Enter the following:

Type: Application

Name: CS 2D (or equivalent)

Command: Navigate to your CS 2D folder, and select the CS 2D launcher for linux using the browse button. In my case:

"/home/5nak3/.cs2d/CounterStrike2D"

Comment: Enter whatever you may see fit

*[COLOR="Red"]Do not press "Ok" yet[/COLOR]*

**Step five:** In the command line of the new launcher we are creating insert a space followed by "-24bit"

This will run CD 2D in 24bit mode. If you want 16bit mode use "-16bit"

Also if you want to run the game in a window instead of fullscreen add "-win" at the end of the launcher.

**Step six:** If done correctly the command should look like one of the following:


/home/<Your Name>/.cs2d/CounterStrike2D -24bit 

/home/<Your Name>/.cs2d/CounterStrike2D -24bit -win

/home/<Your Name>/.cs2d/CounterStrike2D -16bit

/home/<Your Name>/.cs2d/CounterStrike2D -16bit -win

Once you have the command looking like the above. Press "Ok" and launch the game via the application -> Game -> CS 2D option.

---

