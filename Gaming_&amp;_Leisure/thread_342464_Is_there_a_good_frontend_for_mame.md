---
title: "Is there a good frontend for mame ?"
date: 2007-01-20
forum: Gaming &amp; Leisure
---

### Post by burek on 2007-01-20
1/Is there a good frontend for mame ?  

2/Which  game are you playing on mame ? (& you recommand the try )

---

### Post by hikaricore on 2007-01-20
Kxmame works fine, as far as killer instinct, you'll need to modify my information here:

[http://ubuntuforums.org/showthread.php?t=307728&highlight=chd](http://ubuntuforums.org/showthread.php?t=307728&highlight=chd)

To fit your particular game.

A simple search of google for "mame chd" or something of the like would have solved this issue for you.  I doubt you actually own a full KI1 arcade box so keep the illegal discussion at a minimum here please.  And before you contest this, there's no such thing as 24 or 48hrs to delete the rom files, it's all just crap.

---

### Post by burek on 2007-01-20
i tried gxmame, and installed the deb

ok, 

in ALL GAMES, there is nothing into ... ](*,) 
rebuild game list gives no changes
thou have any idea ?

thank you

---

### Post by hikaricore on 2007-01-20
..... you do know how to read am I correct?

---

### Post by kori.mendocino on 2007-04-10
hikaricore, you are being rude. Let's be more careful about how we communicate around here, unless of course you are more interested in licenses.

---

### Post by cor2y on 2007-04-10
burek you need the beta version of gxmame 0.35 beta2 for it to work.
Get it here 
Source
[http://sourceforge.net/project/showfiles.php?group_id=50621](http://sourceforge.net/project/showfiles.php?group_id=50621)
Deb or Source
[http://linux.softpedia.com/progDownload/GXMame-Download-3437.html](http://linux.softpedia.com/progDownload/GXMame-Download-3437.html)

Also if after this you try to run mame and you get a black screen and keyboard lockup that requires a hard reboot

Try this method to fix it.
This applies to ATi cards and if you are using xmame
> 
sudo apt-get install xmame-sdl xmame-tools xmame-common

Install your frontend
Now before running xmame or gxmame do this
via terminal
> 
xmame --showconfig > ~/.xmame/xmamerc
Now run your frontend or xmame from the terminal

No more black screen.

---

