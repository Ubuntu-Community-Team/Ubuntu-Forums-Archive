---
title: "How to Uninstall Games!!!???"
date: 2008-05-15
forum: Gaming &amp; Leisure
---

### Post by elmaster84 on 2008-05-15
Ive been downloading bunch of games. All of them work but since my laptop is Vista :oops::mad:/UBUNTU :guitar: Dual Boot I ran out of space. I need to uninstall some games but haven't got the slight less idea on how to do it!!!...any help..Ill be Gratefull!!!
List of games I want to uninstall:
Ultimate Stunt
Atomik Tanks
Nimuh
Tennix
BOS wars
PainTown

Please remember I'm new to Ubuntu, so I need detailed Instructions on HOW TO!!!...THNX!!!

---

### Post by MaindotC on 2008-05-15
Hi, elmaster84.  There are a couple of ways to uninstall the games.  If you installed them from the Ubuntu menu by navigating to Applications -> Add/Remove then you can type in the name of the game you installed and select the checkbox to have it removed.

However, I had trouble finding the name of the games you listed in the Add/Remove menu so it looks like you may have downloaded debian package installers.  If you know the name of the package that installed the game on your system, you can uninstall it by opening a command prompt and typing:
```

sudo dpkg -r package_name

```
where package_name is the name of the package you installed.  If you have trouble locating the package, you can search for it by typing:
```

sudo locate .deb | more

```
The debian packages you download are either in the directory you specified in your web browser, or they're usually in /var/cache/apt/archives.  Let me know how it goes!

---

### Post by elmaster84 on 2008-05-15
THNX for the fast response!!!!!
Ive managed to uninstall all of the games except 1

Ultimate Stunts

I gave a Right click over applications-->Edit Menus-->GAMES, then right click over the game's icon and on the command prompt is written

ustunts

So I typed, 
```
sudo dpkg -r ustunts
```
and this is what I got
```
dpkg - warning: ignoring request to remove ustunts which isn't installed.

```

Probably I'm doing something wrong. So if you could help once more..:guitar:

---

### Post by Perfect Storm on 2008-05-15
How did you install it?

---

### Post by elmaster84 on 2008-05-15
Just one small thing..aparently Atomic Tanks wasnt uninstalled either. 

I got both games from this page...GetDeb.net

[http://www.getdeb.net/app/Ultimate+Stunts](http://www.getdeb.net/app/Ultimate+Stunts)
[http://www.getdeb.net/app/atanks](http://www.getdeb.net/app/atanks)

this are both games. You just download them, doble click and done. No hastle. But thats the reason I dont know how they were installed.

---

### Post by Perfect Storm on 2008-05-15
Open synaptic and search for them should give you some hits.

---

