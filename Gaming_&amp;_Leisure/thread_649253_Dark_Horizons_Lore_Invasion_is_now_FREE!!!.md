---
title: "Dark Horizons: Lore Invasion is now FREE!!!"
date: 2007-12-24
forum: Gaming &amp; Leisure
---

### Post by autocrosser on 2007-12-24
Yes, you heard me!!! Go & grab a free download!!!

[http://www.garagegames.com/products/29/](http://www.garagegames.com/products/29/)

[B]:guitar:
[/B]

---

### Post by DARKGuy on 2007-12-24
Where's the download link? I can't find it! :(

---

### Post by autocrosser on 2007-12-24
Link is the "free download" icon---but here's the page link:

[http://www.garagegames.com/pg/demo.php?id=29](http://www.garagegames.com/pg/demo.php?id=29)

Remember to grab the Serial# from the main page to unlock the game....

I just installed it: you need to chmod a+x (location of file) & then do a sudo (location of file) to run the installer.

---

### Post by autocrosser on 2007-12-24
Haven't got it to run yet--post your results everyone!!

---

### Post by The Noble on 2007-12-24
It's not starting for me. I guess it is missing some dependencies.

---

### Post by Vadi on 2007-12-24
Per this site: [http://www.linuxgames.com/archives/9861](http://www.linuxgames.com/archives/9861) they'll be releasing a new linux installer.

I don't know though, it worked perfectly fine for me - I just had to run it from the terminal though, it refused to launch otherwise. But it installed & plays perferctly.

The game is really fun, and works on pretty old cards too. My only regret is I guess not being able to buy it.

---

### Post by autocrosser on 2007-12-25
I make a script to start the game---real simple, looks like:

cd "/usr/local/games/DHLore" && exec ./DHLore.bin

do a chmod +x (location of the script)

and referenced a launcher to it---works great now!!

Not that I've played it--I remember playing it with my macs several years ago....

---

### Post by cogadh on 2007-12-25
Well, I got nothing. The game can install and launch, but segfaults when I try to start a game. I did find that I have to "bash" the launch script that the game installs, otherwise it produces an extra error, but it still won't run:

Just running the launch script:
```
cogadh@kubuntu-matrix:~$ dhlore
[: 107: ==: unexpected operator
fcntl: Operation not permitted
fcntl: Operation not permitted
Segmentation fault (core dumped)
```
Using bash to run the launch script:
```
cogadh@kubuntu-matrix:~$ bash dhlore
fcntl: Operation not permitted
fcntl: Operation not permitted
Segmentation fault (core dumped)
```
I know that the "fcntl" is some kind of file control error, but I've never seen it before, so I'm not sure where to start troubleshooting it.

---

### Post by autocrosser on 2007-12-25
Try chmod a+x on the /usr/local/games/DHLore.bin & see if that fixes it for you---

---

### Post by Vadi on 2007-12-25
I installed it in my home dir btw, not system-wide.

---

### Post by cogadh on 2007-12-25
> **autocrosser said:**
> Try chmod a+x on the /usr/local/games/DHLore.bin & see if that fixes it for you---
It's already executable, the game does actually launch, it just crashes with a segfault when I try to start an instant action game.
> **Vadi said:**
> I installed it in my home dir btw, not system-wide.
I'll give that a shot next.

---

### Post by DARKGuy on 2007-12-25
Three words:

THIS.

GAME.

ROCKS!!!!

---

### Post by autocrosser on 2007-12-26
Interesting--I used the installer & did a system-wide--using Hardy & after I created the script, I've had 0 problems using it...Yse I'd try installing to /home--maybe the installer is a bit buggy & I just got a good install.

---

### Post by k0rfain on 2007-12-26
is this just a demo
?

---

### Post by autocrosser on 2007-12-26
look at the main page---there is a serial# that is for the free one....

---

### Post by Dark Hornet on 2007-12-26
> **cogadh said:**
> Well, I got nothing. The game can install and launch, but segfaults when I try to start a game. I did find that I have to "bash" the launch script that the game installs, otherwise it produces an extra error, but it still won't run:

Just running the launch script:
```
cogadh@kubuntu-matrix:~$ dhlore
[: 107: ==: unexpected operator
fcntl: Operation not permitted
fcntl: Operation not permitted
Segmentation fault (core dumped)
```
Using bash to run the launch script:
```
cogadh@kubuntu-matrix:~$ bash dhlore
fcntl: Operation not permitted
fcntl: Operation not permitted
Segmentation fault (core dumped)
```
I know that the "fcntl" is some kind of file control error, but I've never seen it before, so I'm not sure where to start troubleshooting it.


Well--I get the exact same thing...I can launch the game just fine, but when I go to "Instant Action", the game crashes (core dumped) with the same errors.

---

### Post by Sockerdrickan on 2007-12-26
I'll try it, is it the "demo" download?

---

### Post by Vadi on 2007-12-27
No, this is a full game.

Maybe you guys are missing some library? (I have a ton of them installed, not really picky about all of the depenency things)

---

