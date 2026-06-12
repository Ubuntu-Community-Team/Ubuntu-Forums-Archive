---
title: "switching back to desktop during a game ?"
date: 2007-03-19
forum: Gaming &amp; Leisure
---

### Post by rajeev1204 on 2007-03-19
Hi

i want to know how to switch back to desktop in the middle of a game or something? 

For example when playing quake 4 





regards

rajeev

---

### Post by Monk-e on 2007-03-19
Depends on the game. It's not possible in Quake 3. It might just be alt+tab for quake 4.

---

### Post by rajeev1204 on 2007-03-19
hmm alt tab doesnt work .

I think thats important feature to have .In windows u just have to press the windows key on the keyboard


strange that ubuntu doenst have that

---

### Post by bastiegast on 2007-03-19
I agree, ubuntu, or the linux desktop in general, should have something like that easily accessible. 
That does not mean however that it's not possible, you can do it even better, for example by starting a different X server for the game. You can then switch from game to desktop with ctrl-alt-F7 and ctrl-alt-F9.

I believe you can start the X-server with ```
X :1.0
```
Then open a new terminal(ctrl-shift-tab in gnome terminal) ```
export DISPLAY=:1.0
quake4 (or other game)
```

I know this is far from user friendly but it allows you to switch between desktop and game way faster than windows can.

---

### Post by lakersforce on 2007-03-19
Ctrl+Alt+Esc switches you back to gnome desktop. Always works!

---

### Post by Cappy on 2007-03-19
I use ETSWITCH 
[http://hem.bredband.net/b400150/](http://hem.bredband.net/b400150/)
You run it before you run your game and you can use [Win Key] + Z to minimize.

I just tried the export X thing with ut2004. After I started X I had to goto my tty2 to export and start ut2004. The Alt + Ctrl + Tab didn't do anything.
The splash screen then came up but then the program quit with an error of "Couldn't set video mode: Couldn't find matching GLX visual"

Finally, I tried Ctrl+Alt+Esc and it didn't minimize ut2004 (I ran it the normal way), it only asked if I wanted to quit.

I guess ETSWITCH for me =P

---

### Post by kvonb on 2007-03-19
The simplest method (although a little slow) is to drop the console and press <CTRL><ALT><ENTER>

Or as I sometimes do, set the option "Fullscreen" to "No".

Of course in this case you need to be running a desktop res that is higher than the game res.  I use 1600x1200 for my desktop, and run Enemy Territory (which I believe is based on the Quake3 engine) at 1280x1024, it sit's happily on the desktop :).

---

### Post by Khaled Khalil on 2007-03-20
ETSwitch works fine for quake4 like [Cappy said]("http://ubuntuforums.org/showpost.php?p=2324469&postcount=6"), but not for battle for wesnoth and all my favorite games :( 
also alt+enter and ctrl+F11 works for some games and not others
alt+ctrl+esc return to desktop, but kill the game :( 

i think bastiegast's [suggestion]("http://ubuntuforums.org/showpost.php?p=2322957&postcount=4") would be great, but if i understood it :oops: 
sorry bastiegast, i need more explanation, do you mean starting the new X server (X :1.0) from another tty than 7 or any terminal (under desktop)
(what is the 1 and what is the 0 ?, i found no manual by "man X")
i did this and switched to ctrl+alt+F9, yes there was an X server running as i noticed black X cursor on grey background, but no desktop nor terminal
then write the "export DISPLAY=:1.0" in terminal of the original desktop (alt+ctrl+F7) :confused: 
then after submiting the game's name (wesnoth), i got this:
Battle for Wesnoth v1.1.8
Started on Wed Mar 21 02:33:33 2007

started game: 1911141496
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified


       ---------------------- DirectFB v0.9.24 ---------------------
             (c) 2000-2002  convergence integrated media GmbH  
             (c) 2002-2004  convergence GmbH                   
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2006-10-13 15:40) 
(*) Direct/Memcpy: Using MMXEXT optimized memcpy()
(!) Direct/Util: opening '/dev/fb0' failed
    --> Permission denied
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
error display: Could not initialize SDL: DirectFBCreate: Initialization error!
Could not initialize video. Exiting.

](*,)

---

### Post by hikaricore on 2007-03-20
> **bastiegast said:**
> I agree, ubuntu, or the linux desktop in general, should have something like that easily accessible. 
That does not mean however that it's not possible, you can do it even better, for example by starting a different X server for the game. You can then switch from game to desktop with ctrl-alt-F7 and ctrl-alt-F9.

I believe you can start the X-server with ```
X :1.0
```
Then open a new terminal(ctrl-shift-tab in gnome terminal) ```
export DISPLAY=:1.0
quake4 (or other game)
```

I know this is far from user friendly but it allows you to switch between desktop and game way faster than windows can.

A simpler version of the above mentioned tip is found here:

[http://help.ubuntu.com/community/WorldofWarcraft#head-5bcf9267027c1ff9001b3e20c9e3128232cd5a7d](http://help.ubuntu.com/community/WorldofWarcraft#head-5bcf9267027c1ff9001b3e20c9e3128232cd5a7d)

This can be adapted to fix almost any native or wine based game.  In fact, I personally use similar scripts to launch atleast 6 games.

There is also a gtk application somewhere in existance that give this process a gui, and allows you to launch any application on whatever "screen" you want.  The project is currently dead to the best of my knowledge but you can find it linked to from here: [http://happypenguin.org/show?Xgame](http://happypenguin.org/show?Xgame)

---

### Post by hikaricore on 2007-03-20
Hmm... it appears that even the site for Xgame is dead, so I'm attaching it here in the odd chance that someone might find it useful.   (I keep everything I come across lol)

---

