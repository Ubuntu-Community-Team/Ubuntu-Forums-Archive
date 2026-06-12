---
title: "How to install gnome desktop environment?"
date: 2008-08-25
forum: Desktop Environments
---

### Post by harrybazeegar on 2008-08-25
Hi,
I have been using Ubuntu Desktop Edition for quite a long
time, but I have never really found out how to install gnome
on a "brand new" linux.

So I installed Ubuntu Server edition... Now I tried to install gnome on it... So what packages do I have to install to set up a gnome desktop environment?

What is the meaning of X server? what does it have to do with gnome, or any windowed environment for that matter?

I tried install gdm (sudo apt-get install gdm), and it succeeded too.
But i dont see any login manager when I type "sudo gdm".
When nothing happenned after "sudo gdm", I went tty7 (alt+f7) but nothing was present there (just a blinking cursor). I guess I'm missing something. Please help me. This is the request of a die-hard ubuntu fan :)

BTW, I'm using elinks right now. God, its so hard to get anything done on it!

---

### Post by ooobuntooo on 2008-08-25
Why do you need a GUI on a server?

---

### Post by harrybazeegar on 2008-08-25
Well, I installed the server just because it comes without a GUI. 
In theory, I would have installed any linux that did _not have a GUI_.

What I actually want to know is how to install a GUI, not why I don't need a GUI on a server.

---

### Post by mcduck on 2008-08-26
"sudo apt-get install ubuntu-desktop" will install everything you need.

If the GDM doesn't start automatically, run "sudo /etc/init.d/gdm start".

X Window System provides all the tools & protocolls graphical desktops need to work, like drawing programs into windows on screen, mouse & keyboard interaction etc.. (but it _doesn't_ provide any user interface, that's what the window managers/desktop environments are for).

---

### Post by harrybazeegar on 2008-08-26
That's exactly what I dont want to do!

I know I can install "ubuntu-desktop", and get everything readymade. But what if this wasn't a debian based system? What if I (God forbid) hated ubuntu and didn't want to install it this way??

I want to know hows its done manually. I want to do it by hand!!

Please, anybody?? :(

---

### Post by mcduck on 2008-08-26
If "by hand" means that you don't want to use the package manager then it's lots of compiling from source code for you :)

I suppose you should start by downloading & compiling X, GDM and all base Gnome packages & their dependencies.

---

### Post by sspl08 on 2008-08-26
If you have installed opens Use with the default selections of choosing one of the available then only the selected Desktop environment is installed.However,should you later choose to install and use another desktop Environment say then this can easily be installed and as always just a few clicks away.
sam


[Arkansas Alcohol Addiction Treatment](http://www.alcoholaddiction.org/arkansas)

---

### Post by jedi-penguin on 2008-08-26
try "apt-get install gnome2"
then "startx"

---

