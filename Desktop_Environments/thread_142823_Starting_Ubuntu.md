---
title: "Starting Ubuntu"
date: 2006-03-11
forum: Desktop Environments
---

### Post by dyvasey on 2006-03-11
I am definitely a total noob at linux and ubuntu. I've gone throught the whole install process with ubuntu and now I get a black screen that asks for my user name and password. After typing those in, the line says my login@something: ~$. Then, it waits for me to type something. What should I do next?

---

### Post by kittycatsexycat on 2006-03-11
in that space write:

startx

that is the desktop...:KS or maybe with a space like : start x

---

### Post by Sef on 2006-03-11
sounds like you did a server install, which doesn't download the gnome desktop.

1. Were you connected into the internet when doing the install?

2.  If yes, are you connected now to the internet?

3. if so, do this:  Applications ---> Assossories ----> Terminal ---> sudo apt-get install gnome-desktop ----> enter -----> password ----> and follow the directions.  type y and enter if it asks you to.

---

### Post by dyvasey on 2006-03-11
When I type in startx, I get a bunch of weird errors, ending with "X: user not authorized to run the X server, aborting."

---

### Post by dyvasey on 2006-03-11
No, I wasn't connected to the internet and I still am not. Do I need to be?

---

### Post by taurus on 2006-03-11
[QUOTE=Sef]sounds like you did a server install, which doesn't download the gnome desktop.

1. Were you connected into the internet when doing the install?

2.  If yes, are you connected now to the internet?

3. if so, do this:  Applications ---> Assossories ----> Terminal ---> sudo apt-get install gnome-desktop ----> enter -----> password ----> and follow the directions.  type y and enter if it asks you to.[/QUOTE]
But if he did a server install, how the heck could he open a terminal from the method above???  :rolleyes:   

Why open a terminal when he IS already at the terminal...

---

### Post by stanz on 2006-03-11
Hi All,
Yeah, I don't know to much, but i thinks he needs a "Re-install".
When ya began install...did ya press 'Enter" or something else?
Do ya see any ubuntu type screens or jus` prompt commandline?

I don't belive you had the chance to setup internet access, to even try: 
[I]apt-get install gnome-desktop
[/I]but- if your installation cd is still in drive...? It be the only addy in the */etc/apt/sources.list *
which might work- but heck, a total "re-format & re-install" be my choice of fix.

---

