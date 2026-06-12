---
title: "Can't install games from the internet."
date: 2018-11-14
forum: Gaming &amp; Leisure
---

### Post by malikiag on 2018-11-14
So I am a hardcore gamer, and there are a ton of games to get and download. Unfortunately, every time I download a game, my unarchiver activates, unarchives it, and it does nothing. I don't know what to do about it. Is there something different about Bionic Beaver than the versions I used to use? Also, the games that require Wine, Winetricks, and PlayOnLinux, I can't do anything with. I download a file, and I'm not given the option to install it. My father tried to install Razor for Ultima Online via terminal, and it installed, but I get a Fatal Error prompt when ever it loads, and can't play. Are we doing something wrong? The websites I get the games from say that it should be working.

---

### Post by oldrocker99 on 2018-11-14
Have you considered installing Steam?
```
sudo apt install steam
```

---

### Post by mastablasta on 2018-11-15
> **malikiag said:**
>  I download a file, and I'm not given the option to install it. 

what do you mean? in play on linux you use their wizzard to install /add the game.

with wine you use terminal. you go to the folder where the game is located and then:

```
wine install.exe
```

or

```
wine setup.exe
```

whatever runs the install.

also not all games run in wine. check compatibility rating:  [https://appdb.winehq.org/](https://appdb.winehq.org/)
gold and platinum rating are ok, silver is a maybe. everything else is not worth bothering. Razor has bronze rating at best. but ultima online has platinum: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=228](https://appdb.winehq.org/objectManager.php?sClass=application&iId=228)

---

### Post by oldrocker99 on 2018-11-15
When using PlayOnLinux, you look for the game you want to install. Each game has its own installation script. It will show a "browse" button to find the .exe file, and will install it. If you have Windows games on GOG, it'll ask for your GOG.com password, and download and install the file automagically.

---

### Post by jastiv on 2018-11-30
My favorite is ./configure make make install, but with Wograld there are a couple extra steps.  If you really want to be an alpha tester though, I suggest you ignore "releases" and git them directly from git.

---

