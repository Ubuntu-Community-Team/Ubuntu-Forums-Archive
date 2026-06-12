---
title: "Fullscreen games Alt-Tab/Minimize?"
date: 2007-06-01
forum: Gaming &amp; Leisure
---

### Post by Hellcom on 2007-06-01
Is there any way to minimize or move to another workspace from a full screen game? Its annoying if I want to send a message via irc, check on some other process, change a setting etc... while playing a full screen game as the only thing I can do is exit the game, which isn't very viable is many situations.

Ubuntu 7.04 Gnome/Metacity
ATI 9800 Pro 128MB with ATI closed sourced drivers

---

### Post by aidanr on 2007-06-01
look up etswitch or xgame/xgame-gtk2

---

### Post by Hellcom on 2007-06-01
I installed etswitch, but I can't figure out how it works (hotkeys, etc...) as I can't find any documentation other than how to compile and install. Xgame looks really promising, but it doesn't look like the project exists anymore:

 [http://xgame.tlhiv.com/](http://xgame.tlhiv.com/)

Can anyone help me further?

---

### Post by Cappy on 2007-06-01
> **Hellcom said:**
> I installed etswitch, but I can't figure out how it works (hotkeys, etc...) as I can't find any documentation other than how to compile and install. Xgame looks really promising, but it doesn't look like the project exists anymore:

 [http://xgame.tlhiv.com/](http://xgame.tlhiv.com/)

Can anyone help me further?

It's either Control+Z or Alt+Z, I forgot which (while ETswitch is running, of course - should be under Applications-->Games or probably could be run with "etswitch"). 
Each game usually has its own "minimizing" key combination. For instance, in UT2004 I use ALT+ENTER and then Control+G. In WINE I have to press PrintScreen, although ETSwitch may work with WINE also. I havn't reinstalled ETswitch so I'm not sure.

---

### Post by Hellcom on 2007-06-01
> **Cappy said:**
> It's either Control+Z or Alt+Z, I forgot which (while ETswitch is running, of course - should be under Applications-->Games or probably could be run with "etswitch"). 
Each game usually has its own "minimizing" key combination. For instance, in UT2004 I use ALT+ENTER and then Control+G. In WINE I have to press PrintScreen, although ETSwitch may work with WINE also. I havn't reinstalled ETswitch so I'm not sure.

So it only works with the games supported? That sucks, as the game I currently play the most is not on that list :/

---

### Post by aidanr on 2007-06-01
here's the xgame scripts

there's a how-to [here]("http://ubuntuforums.org/showthread.php?t=51486&highlight=xgame") you have to follow first to be able to start a new xserver

---

### Post by DonPeppe on 2007-06-01
I'm not sure about minimizing to the desktop, but I use ctrl+alt+TAB to open the top/bottom panel of my GDE from witihin World of Warcraft.  it works without installing anything else on Ubuntu.

What I do then is I open the program I want to open from the menus or click on the "show desktop" shortcut (bottom left) if I need to run a shortcut on the desktop.   So far it has worked for me.  Maybe try it on your game and report back if it helps.

---

### Post by tL0z on 2007-06-03
I'm having a similar problem. Alt+enter works for Warsow but it only puts the game in window mode. I can't chage to another window.

Any idea?

---

### Post by tL0z on 2007-06-04
There isn't any gamer who likes to minimize his games? :P

---

### Post by tL0z on 2007-06-09
hello?

---

### Post by jeteir on 2007-09-08
Yeah, I'm having this problem with OpenArena too, on GDE.

And really I don't think that that is a good idea about starting new X server per game neither game-dependent minimization is.

I guess it depends on a window manager, thus, anybody has such a problem on KDE or other WM?

---

### Post by matthiasak on 2008-04-13
hey, i just figured it out! 

atleast for warsow, just bring up the console (~) and alt tab

---

### Post by bogdanbiv on 2008-06-08
Hello, I have the same problem with Battle of Wesnoth.

Global shortcuts don't work in fullscreen games because the Xserver sends all input from the keyboard to the game itself. It doesn't matter if you run KDE or Gnome or other Desktop Env. 
I have found only one shortcut that does work as normal:
DON'T TRY it just yet! Save your programs because it kills all your graphical  environment programs and your session.

Ctrl + Alt + BackSpace kills the X server.
The (best) solution would be to define another (new) shortcut that is sent to the window manager irrespective of what application has control (is fullscreen).

This would be independent of the game running, but I haven't figured how to actually one can do it.

---

### Post by Cappy on 2008-06-08
Someone made an ubuntu specific script similar to xgame,
[http://ubuntuforums.org/showthread.php?t=699332](http://ubuntuforums.org/showthread.php?t=699332)
which runs the game in a separate X session allowing you to switch back and forth on any program.

---

### Post by Pasdar on 2009-12-25
IMO the best way is to just open a program in the background... like just open the file browser or terminal whatever... then when you're in the game, just ALT-TAB to it... the only moment that doesnt really work for me is when the program that I opened in the background is fullscreened... so dont fullscreen it... jus have it open in the background.

I added a shortcut for return to desktop (Windows + D), but that doesn't work... at least not in HoN..

---

