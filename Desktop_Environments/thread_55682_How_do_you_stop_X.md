---
title: "How do you stop X?"
date: 2005-08-09
forum: Desktop Environments
---

### Post by DeathOnJuice on 2005-08-09
Hey, everyone. I want to be able to stop GNOME so I can have only one application (a game) running in X (so it will go faster). I figured the easiest way to do this is to stop X all together and then use xinit to run the game without starting GNOME. I already have it down how to start a new X session only running the game, but I want to exit the X session running GNOME. I know I could stop it from running in the first place by editing /etc/inittab, but for reasons I don't have to explain I can't do that. So, here's what I've tried:

I tried switching to a virtual terminal (with Control+Alt+F1) and using the init 3 and telinit 3 commands. After both commands, I pressed Control+Alt+F7 and sure enough, my desktop manager was still running. I figured that maybe switching to runlevel 3 only stopped X from starting in the first place, but it doesn't end it. So, I pressed Control+Alt+Backspace, which is supposed to restart X, hoping it would end but not start again. It did start again, of course.

So, does anyone know how to stop X?

---

### Post by PeP on 2005-08-09
sudo /etc/init.d/gdm stop

replace gdm by kdm on kubuntu

---

### Post by tread on 2005-08-09
log out of gnome, then login in failsafe X mode (I'm pretty sure this exists). Then from the terminal, start your game.

---

### Post by DeathOnJuice on 2005-08-09
[QUOTE=tread]log out of gnome, then login in failsafe X mode (I'm pretty sure this exists). Then from the terminal, start your game.[/QUOTE]
 To PeP: when I do that, it says:

 * Stopping GNOME Display Manager...
 * GNOME Display Manager not running                                     [ ok ]

I know GNOME is running, though (I changed the WM from Metacity to E16 using a topic on this forum, but GNOME is still running), and it continues to run. Also, I don't want to replace GNOME, I just want to know how to kill it when I need to.

To tread: That's almost what I want, but that starts Xterm. I need it to look like the virtual terminals you get to by pressing Control+Alt+F(NUMBERHERE). That means X shouldn't be running at all. Then, I could execute "xinit /usr/games/GAMEHERE $* -- :1" and X would only be running the game, nothing else.

---

### Post by PeP on 2005-08-09
dpkg-reconfigure gdm tells you wich manager you use and allows you to change it.

if it's kdm
/etc/init.d/kdm stop
if it is xdm
/etc/init.d/xdm stop

ps- aux shows you everything running on your system also.

---

### Post by tread on 2005-08-09
>  I could execute "xinit /usr/games/GAMEHERE $* -- :1" and X would only be running the game, nothing else. 

Well, you need to stop gdm for that .. I think someone already replied to that. Try running it from xterm though, because xterm is really low on resources.

---

### Post by linuxa on 2005-08-19
<Sorry, posted in the wrong thread>

---

