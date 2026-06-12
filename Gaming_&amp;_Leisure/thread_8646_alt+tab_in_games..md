---
title: "alt+tab in games."
date: 2004-12-19
forum: Gaming &amp; Leisure
---

### Post by AndersAA on 2004-12-19
Any hotkey app that'll allow me to use alt+tab or alt+f9 to minimize) a full screen 3d application?

I really like to be able to check icq messages for example while gaming (and full screen gaming), I've been running another X session for it sometimes, but... it'd be more practical to have a working hotkey ;)

---

### Post by soritong on 2004-12-22
[QUOTE=AndersAA]Any hotkey app that'll allow me to use alt+tab or alt+f9 to minimize) a full screen 3d application?

I really like to be able to check icq messages for example while gaming (and full screen gaming), I've been running another X session for it sometimes, but... it'd be more practical to have a working hotkey ;)[/QUOTE]
 As stated [here](http://www.linuxquestions.org/questions/history/258743):

It's possible to switch to windowed mode while running UT2k4, just press Alt-Enter to toggle back and forth between fullscreen and windowed. The only problem with this is the mouse remains grabbed by the UT2k4 window. To work around that you can add

```
Option "AllowDeactivateGrabs" "true"
```

to the ServerFlags section of your xorg.conf or XF86Config file.
If you dont have a ServerFlags section in your conf file it should look like this

```
Section "ServerFlags"
        Option "AllowDeactivateGrabs" "true"
EndSection
```

Once X has been restarted you can use Ctrl-Alt-numpad_divide key to ungrab the mouse.

---

### Post by AndersAA on 2004-12-22
works in some games, but not all games, it'd be nice to have a hotkey to minimize full screen apps that's unable to go window mode.

I'll try alt+enter though, didn't think about that earlier, might work in some of em.

---

### Post by graigsmith on 2005-08-09
anyone know of a universal way to minimize a 3d game?  or possibly run a 3d session on another virtual session?  like if i am currently running on ctrl-alt-f7, is there any way to start the game on ctrl-alt-f8.

i have tried getting the game to run on f8, but it seems that the first gdm session uses the 3d part of the card and locks it.  so any other games, or gdm sessions after the first one launched CAN"T use 3d.    is there any way to force the first gdm NOT to use 3d, so i can start the game in its own 3d session?

---

### Post by ubernoob on 2007-01-20
The example above didn't work for me, but I found etswitch which does the job.  

[http://gentoo-wiki.com/HOWTO_minimize_fullscreen-Games]("http://gentoo-wiki.com/HOWTO_minimize_fullscreen-Games")

Home page for etswitch:
[http://hem.bredband.net/b400150/]("http://hem.bredband.net/b400150/")

Download latest code and do this:

```
tar xvzf etswitch-0.1.14.tar.gz
cd etswitch-0.1.14/
./configure --prefix=/usr
make
sudo checkinstall
sudo dpkg -i etswitch_0.1.14-1_i386.deb
```

Run "etswitch -c" to configure which key to bind.

Run the program before you start the full screen app. Use key to switch back and forth from X and game.

You can also make a new startup script like this one i use for America's Army:

I made this file in /opt/armyops/armyops-startup
```
#!/bin/sh
etswitch -ng -nw &
aoss /opt/armyops/armyops
killall etswitch
```

(PS: the aoss is an alsa-oss wrapper. Not needed, but if you want it, do "sudo apt-get install alsa-oss")

---

### Post by minisori on 2007-01-21
You can also run the game in another X server, so then you are able to change between them fast and without problems.

sudo X :1 -ac & DISPLAY=:1 game_binary

---

