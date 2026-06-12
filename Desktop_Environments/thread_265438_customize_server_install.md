---
title: "customize server install"
date: 2006-09-26
forum: Desktop Environments
---

### Post by comppsyco on 2006-09-26
Hi all,
For reasons that I won't go into here, I had some problems for which it was going to be easier to just re install ubuntu than to try to fix them, and all my data's on another partition, so I was safe.
I'd been reading about doing a server install, then customizing it to get a compact, lightning-fast system. So I did a server install, and went to install a desktop environment. But I realized that installing ubuntu-desktop (I like gnome, although I've never used xfce, fluxbox, windowmaker, icewm, etc, do they provide a big enough speed gain to be worth it?), and I realized that it would install a bunch of programs that I don't want. Basically, I want this: gnome (maybe with xgl, although I've had problems galore with this), firefox (preferably 2.0, with the ability to watch youtube movies, etc.) abiword, gedit, and to be able to install other stuff from there, when I need it. So what packages should I install? How do I get x and gnome without ubuntu-desktop?

---

### Post by comppsyco on 2006-09-26
I've been looking at those window managers, and fluxbox looks the coolest, but is there a way to get it to work with a deskbar type of thing?

---

### Post by comppsyco on 2006-09-26
Okay, so I did a clean server install, then installed the package fluxbox. When I try "startx" it can't find the command. When I try "fluxbox" it says that it can't connect to x server. Why?

---

### Post by kerry_s on 2006-09-26
You need the x system to.->

sudo apt-get install x-window-system-core gdm xterm

a good deskbar is xfce4-panel

sudo apt-get install xfce4-panel  

there are others but the xfce one is easy to customize and dosen't have alot of apps that don't work.

---

### Post by Gentleman on 2006-09-30
For a few months now I am a happy Arch-Linux user. (Arch will never leave my hard disk) I used Ubuntu before but I don't like prepacked distro's with many software and preconfigured stuff. As a real linux user I want to try another distro once a while... I noticed Ubuntu is really evolving and would like to try it again. As a said before I won't choose the standart installation but would prefer the server installation.
before I start seting up I have a few questions. 

- Can you build a normaal gnome-desktop without installing "ubuntu-desktop + everything on it"
- What schould I install and configure for the best performance?
- Isn't debian a better solution for my needs? (or is'nt this up-to date at all?)
- Other tips?

---

