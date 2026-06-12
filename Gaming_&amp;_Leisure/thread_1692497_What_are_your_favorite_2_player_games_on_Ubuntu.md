---
title: "What are your favorite 2 player games on Ubuntu?"
date: 2011-02-21
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2011-02-21
Hello.

What are your favorite 2 player games (both people sitting at same PC) on Ubuntu? I don't refer to multiplayer games such as Nexuiz, Urban Terror, etc.

Thanks.

---

### Post by ubuntu27 on 2011-02-21
[Super Tux Kart]("http://supertuxkart.sourceforge.net/")

[Super Mario War]("http://smw.supersanctuary.net/site/")

Also visit [Super  Mario War extra content]("http://smwstuff.supersanctuary.net/index.php")

---

### Post by Rytron on 2011-02-21
> **ubuntu27 said:**
> 
[Super Mario War]("http://smw.supersanctuary.net/site/")

Also visit [Super  Mario War extra content]("http://smwstuff.supersanctuary.net/index.php")

Thanks for posting. How do I start Super Mario War? There is also a download here [here]("http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Arcade/Super-Mario-War-11293.shtml"). It downloads a .tar.gz file and once extracted there is a folder named 'usr' Then within a subfolder called 'games', there are 3 executables called [COLOR="Indigo"]smw[/COLOR], smw-leveledit, smw-worldedit. When I click on smw, it wont start. :confused:

---

### Post by Perfect Storm on 2011-02-21
OpenTyrian: [http://code.google.com/p/opentyrian/](http://code.google.com/p/opentyrian/)
Gish: [http://www.chroniclogic.com/gish.htm](http://www.chroniclogic.com/gish.htm)

Both games support hotseat.

---

### Post by mastablasta on 2011-02-22
liero is also nice :-)
 
there are some nice hotseat strategy games (if you don't mind waiting for the other player to move) available for linux and DOS that work nicelly.
 
hedgewars - linux version of worms :-) i like the original more.

---

### Post by ubuntu27 on 2011-02-22
> **Rytron said:**
> Thanks for posting. How do I start Super Mario War? There is also a download here [here]("http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Arcade/Super-Mario-War-11293.shtml"). It downloads a .tar.gz file and once extracted there is a folder named 'usr' Then within a subfolder called 'games', there are 3 executables called [COLOR="Indigo"]smw[/COLOR], smw-leveledit, smw-worldedit. When I click on smw, it wont start. :confused:

Super Mario War is broken in Ubuntu 10.10.
I used to play in all my previous version of Ubuntu.

SMW requires a library (libpng.so.3) that it is usually not installed by default, but, even if you install it, SMW does not find it.
And if you Symlink that file to the correct version of the library, it simply does not work.


I hope that it gets fixed in Natty.

Here is the bug report: 

[https://bugs.launchpad.net/libpng/+bug/284325](https://bugs.launchpad.net/libpng/+bug/284325)

EDIT: They say that it got fixed.. Since I am still experiencing the same problem, I believe that they fixed it for the next version of Ubuntu, Natty.

*********

EDIT2: Perhaps you are going to have a better luck.
Try to copy each files to its corresponding directory.

For example, the folder "smw" which is under "games" which is under "Share" which is under "usr"
should be copied to **/usr/share/games/**

And there are files that needs to be copied to **/usr/games/**, you know which ones, don't you? ;-)

Same way with the rest, the package that you have downloaded already provides you with the directory.


Now, if you want to run Super Mario War, simply open the terminal and type "smw"

You can create a access link or launcher to the main binary. So make one for /usr/games/smw

---

### Post by Rytron on 2011-02-22
Hi ubuntu27. That is a shame. Yes, lets hope the bug is resolved. Thanks for clearing that up anyway.

---

### Post by Dlambert on 2011-02-22
Wormux

---

