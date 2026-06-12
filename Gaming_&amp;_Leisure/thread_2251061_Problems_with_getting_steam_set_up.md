---
title: "Problems with getting steam set up"
date: 2014-11-01
forum: Gaming &amp; Leisure
---

### Post by gamezoid123 on 2014-11-01
Okay, so I've spent the last three hours trying to get my steam games (For windows, I already have my linux games going) going. I have it set up with two different steams, one for my native linux games, and the other for games that require wine (speciffically terraria). First i tried winetricks which didn't work, and then just normal wine which also didn't work. At this point I'm just kinda frustrated and would like the guidence of another more experienced user to help me out with getting my steam games for windows to run on linux. 
         Thanks, Jacob C.

---

### Post by oldrocker99 on 2014-11-04
Go here:[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html) and download the latest version of PlayOnLinux, which automates the installation of Windows games, as well as Steam for Windows games. Search for the name of the game, and, if it's a Steam game, it will download and install Steam for Windows, from which you can download the game. It worked for Skyrim for me, and I installed Oblivion in the same Steam For Windows window, and both ran perfectly. POL can be installed with the Ubuntu Software Center, or gdebi, or:
```
sudo dpkg -i PlayOnLinux_4.2.5.deb
```
You may have a message that it couldn't be installed. If you do:
```
sudo apt-get -f install
```
This will download any dependencies the program needs and install it properly. This, in fact, works for any program you install that returns an installation error.

If you didn't know about PlayOnLinux before, now you do, and you won't regret using it!

---

### Post by gamezoid123 on 2014-11-16
Thanks awesome! :D this should help a lot

---

### Post by dannyboy79 on 2014-11-17
the huge advantage to using playonlinux is that it can create wine bottles which means it can manage different wine version installations. for example maybe terraria only works in wine version 1.7.22 but there's another game that requires you use 1.7.31. playonlinux allows you to have both wine versions installed. it's all possible without playonlinux BUT using playonlinux makes it all SO MUCH EASIER. very cool stuff!

---

### Post by gamezoid123 on 2014-11-18
@Dannyboy79, How would I go about doing that through steam?

---

### Post by gamezoid123 on 2014-11-18
I thought I'd post this as well "Fatal Error: Shader: failed to creat effect compiler for C:\Program Files\Steam\steamapps\common\BIT.TRIPRUNNER/Shaders/Error.aeshader"
This is what it brings up when ever I try running Bit trip runner.

Terraria won't run either but doesn't show any kind of error message

although I was able to get castle crashers running. Any suggestions for the afformentioned errors though?

---

### Post by gamezoid123 on 2014-11-18
Nvm I wasn't aware playonlinux would be so awesome about running steam games! Thanks guys for your help got it running.

---

