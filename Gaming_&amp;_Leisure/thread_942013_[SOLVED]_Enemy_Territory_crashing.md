---
title: "[SOLVED] Enemy Territory crashing"
date: 2008-10-08
forum: Gaming &amp; Leisure
---

### Post by leutnant on 2008-10-08
Hi, Enemy territory crashes everytime I connect to a server. The crash happens when my computer tries to download files from the server hosting the game. 

I'm sure that the crash is caused by the fact that the "enemy-territory" folder does not have file access set to "read and write." How can I change it? I've tried to do it through the gui:

[[IMG]http://img135.imageshack.us/img135/4642/etmainnm0.th.png[/IMG]](http://img135.imageshack.us/my.php?image=etmainnm0.png)[[IMG]http://img135.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

but when I click "apply permissions to enclosed files," the file access permission reverts back to "--"

Any help?

---

### Post by frodon on 2008-10-09
The following command will give all the needed right for enemy territory :
```
sudo chmod -R +rw ~/.etwolf
```

---

### Post by leutnant on 2008-10-09
Thanks for that. After I put that command into the terminal, I could get into the servers no problem, but then, I would get kicked out due to punkbuster not having write permissions to update itself. I have since realized that if I type "sudo et," everything just works more smoothly.

---

### Post by Perfect Storm on 2008-10-09
My suggestion is that you uninstall ET as it would seems you have installed it as superuser do(by sudo).

Instead install it locally (in you home directory) and without using sudo.
Never run a game with sudo, most games can be installed globally (sudo) and then be run normally. In this case it's not.

---

### Post by leutnant on 2008-10-10
Is there any command to uninstall it or do I just delete the files in the ET folder?

---

### Post by frodon on 2008-10-10
[https://help.ubuntu.com/community/EnemyTerritory#Uninstalling](https://help.ubuntu.com/community/EnemyTerritory#Uninstalling)

This page assume you instaled ET in /usr/local/games/enemy-territory, change this path to the one you used if you used a custom directory.

---

### Post by tm002ly on 2008-10-10
&#23567;&#30333;&#33258;&#20174;&#37027;&#27425;&#8220;&#39321;&#28207;&#20845;&#21512;&#24425;&#8221;&#20107;&#20214;&#21518;&#65292;&#27599;&#22825;&#37117;&#38506;&#30528;&#25105;&#65292;&#32780;&#19988;&#26102;&#38388;&#36234;&#26469;&#36234;&#38271;&#65292;&#19981;&#36807;&#24120;&#24120;&#22312;&#19981;&#33258;&#35273;&#38388;&#23601;&#20250;&#39078;&#30528;&#30473;&#24551;&#37057;&#22320;&#30475;&#30528;&#25105;&#12290;&#25105;&#35828;&#31505;&#35805;&#36887;&#20182;&#20063;&#26410;&#33021;&#20351;&#20182;&#24320;&#24576;&#65292;&#34429;&#26159;&#36731;&#26366;&#36947;&#20154;&#21644;&#30333;&#23567;&#22992;&#30473;&#23431;&#38388;&#30340;&#31070;&#20260;&#65292;&#31505;&#24847;&#20877;&#20063;&#19981;&#33021;&#21040;&#36798;&#30524;&#24213;[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gz.cn)[&#20845;&#21512;&#24425;](http://www.tm203.sc.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gx.cn)[&#20845;&#21512;&#24425;](http://www.tm203.gd.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.hn.cn)

---

### Post by leutnant on 2008-10-11
Danke!

---

