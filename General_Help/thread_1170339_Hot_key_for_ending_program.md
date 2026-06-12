---
title: "Hot key for ending program"
date: 2009-05-26
forum: General Help
---

### Post by Cyborgoat on 2009-05-26
Is there a hot key for ending a program?

I am trying to set up Elisa Media center and it locks up when I go to play a movie.

Thanks.

---

### Post by Sparky-da on 2009-05-26
> **Cyborgoat said:**
> Is there a hot key for ending a program?

I am trying to set up Elisa Media center and it locks up when I go to play a movie.

Thanks.

hi [COLOR=Green]Cyborgoat[/COLOR]
I'm new to [COLOR=DarkOrange]Ubuntu[/COLOR]
but I think Alt+Esc

is this what you are asking for?

---

### Post by ushimitsudoki on 2009-05-26
Alt-F4?

A program you might like is called 'xkill'. It will turn your mouse into an "X OF DEATH!!" and kill whatever window you click on.

It's already in your system, and there is often a panel widget to launch it as well, so you don't have to open up a terminal.

---

### Post by cb951303 on 2009-05-26
I add "Force Quit" applet to my panel. It works like xkill.

---

### Post by _Purple_ on 2009-05-26
If you are running it from CLI, Ctrl + C.

---

### Post by NukeouT on 2009-05-29
Im having the same problem on 9.04. Games im testing out sometimes freeze forcing me to reboot.

Alt + Esc, Ctrl + C, Alt + F4 ... do not work

---

### Post by ushimitsudoki on 2009-05-29
If you are trying to kill a full screen game then you probably want to enable DeactivateGrabs in xorg.conf. There is also DectivateGrabs:

```
Section "ServerFlags"
	Option	"AllowDeactivateGrabs"	"True"
	Option	"AllowClosedownGrabs"	"True"
EndSection

```

With this, then:

CTRL-ALT-KP* will "kill" a fullscreen game
CTRL-ALT-KP/ will release the mouse and keyboard from the fullscreen game

---

