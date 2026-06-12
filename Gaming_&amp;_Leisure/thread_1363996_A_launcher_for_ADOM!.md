---
title: "A launcher for ADOM!"
date: 2009-12-25
forum: Gaming &amp; Leisure
---

### Post by ilppi on 2009-12-25
Heya total noob here, I'm not sure if this is the best place to post this but maybe other gamers can help :)

I figured out how to launch ADOM by going to the terminal (apparently the game must be launched this way), and writing the path to the folder where it is located and typing ```
./adom
```then the game launches. There's an error message that says "ADOM requires at least a 25x77 screen to run on", so I have to stretch the terminal window a bit or the game won't run (more on this later).

So, how do I create a launcher for this thing so I dont need to do all of this every time I run the game, instead of just doubleclicking an icon for the game? I try to right-click my desktop and create a launcher and write something like ```
/home/[username]/Games/adom./adom (that's where the game is)
``` as the launch command but I get an error message that says there's no such file when i try to run it!

Also, even if this would work the screen size would propably be wrong so how do I make it so that the screen is at least 25x77 when the game runs?

Thanks for any help!

---

### Post by Bölvaður on 2009-12-25
Is this a terminal only game?

instead of writing cd ... blablabla and then ./
you can instead put that in a script and keep it somewhere in your path, so that if you just enter the name of the script the game will lunch.


I'll teach you 2 ways.

CLI

open the terminal
```
cd /usr/games
sudo nano **adom**

```

note that **adom** is the text I write every time I want to lunch this script. So having it something you'll remember is better than not.

write this in your document
```
cd /home/**bölvaður**/games/adom
./adom_x86
```
obviously this is entirely different for you... adapt to what you use it for.

Save the document by pressing Ctrl+O and close it by pressing Ctrl+X

let's allow the script to be executable
```
chmod **u**+x test
```
you can also change the u (user) to a (all users)



now pretend you just turned on your computer (with no temrinal running) open the terminal and type ad and press TAB. It will not do anything and if you double click TAB then it will tell you you can either type *add* or *adom*.
So you will write ado and then press TAB and watch it change to adom. Then press enter and see it fail at screensize... so you'll resize the terminal window. But then it will work ^^

---

### Post by ilppi on 2009-12-25
Thanks alot I'll try those out. :)

---

### Post by AckSed on 2010-04-27
The screen size is wrong. What it needs is at least an 80x25 screen. See here:
[http://www.codealpha.net/36/how-to-change-the-gnome-terminal-default-size-ubuntu/](http://www.codealpha.net/36/how-to-change-the-gnome-terminal-default-size-ubuntu/)

> Open Terminal.

Type :```
gksudo gedit /usr/share/vte/termcap/xterm
```Enter your password (root password) if necessary.

Find something like this (yours must be different, just look around line 10):

```
:co#80:it#8:li#24:\
```Change the first and last number. To set the default size to 80 columns x 25 lines:

```
:co#80:it#8:li#25:\
```Save.

Close *every* Terminal.

Open a new Terminal, enjoy!

See also here: [http://ubuntuforums.org/showthread.php?t=119271](http://ubuntuforums.org/showthread.php?t=119271)

---

