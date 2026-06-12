---
title: "Xmms and fonts"
date: 2005-01-05
forum: Desktop Environments
---

### Post by christooss on 2005-01-05
I am having problems with fonts in xmms. The fonts are very small if I open menu. 

I am using IceWM and there seems to be the problems in emelfm. I installed system through mini-ram-how-to

---

### Post by strawberry on 2005-03-06
[QUOTE=christooss]I am having problems with fonts in xmms. The fonts are very small if I open menu. 

I am using IceWM and there seems to be the problems in emelfm. I installed system through mini-ram-how-to[/QUOTE]
 I have exactly the same problem: very small fonts in the xmms menu. Playlist's and player's fonts are fine.
It's on gnome/metacity combo. 
I guess I should install some kind of missing fonts. 
christ, have you found a solution of it?

---

### Post by strawberry on 2005-03-06
There's a solution here:
[http://www.ubuntuforums.org/showpost.php?p=16025&postcount=1](http://www.ubuntuforums.org/showpost.php?p=16025&postcount=1)
Maybe not a perfect one but works... :)

---

### Post by bored2k on 2005-03-06
[QUOTE=strawberry]There's a solution here:
[http://www.ubuntuforums.org/showpost.php?p=16025&postcount=1](http://www.ubuntuforums.org/showpost.php?p=16025&postcount=1)
Maybe not a perfect one but works... :)[/QUOTE]
 Better answer : beep-media-player .

---

### Post by strawberry on 2005-03-07
Thnx, I've changed xmms to bmp. Hope I'll be able to change its skin also.  :roll:

---

### Post by A-star on 2005-03-08
[QUOTE=strawberry]Thnx, I've changed xmms to bmp. Hope I'll be able to change its skin also.  :roll:[/QUOTE]
 bmp can use the classics skins from winamp, normally it can also use the skins xmms can use.

---

### Post by strawberry on 2005-03-08
It suits Ubuntu...
[http://anka.org/henrik/humanxmms/](http://anka.org/henrik/humanxmms/)

---

### Post by flaming_monkey on 2005-03-08
[QUOTE=bored2k]Better answer : beep-media-player .[/QUOTE]
 Thanks for pointing me in BMP's direction.  I always like to have native GTK apps, although it's a shame about the messed up playlist buttons (when clicked on they appear in the top left of the screen).

---

### Post by bored2k on 2005-03-08
[QUOTE=flaming_monkey]Thanks for pointing me in BMP's direction.  I always like to have native GTK apps, although it's a shame about the messed up playlist buttons (when clicked on they appear in the top left of the screen).[/QUOTE]
 You need better repositories for the GOOD one. The latest version is about a gazillion times better .

deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports-staging main universe restricted multiverse

apt-get update then update beep-media-player, all that is fixed.


[BMP Plugins](http://www.sosdg.org/%7Elarne/w/Plugin_list)  <-- edit -- > If some plugins dont want to install, download beep media player's development package.

---

### Post by flaming_monkey on 2005-03-09
[QUOTE=bored2k]You need better repositories for the GOOD one. The latest version is about a gazillion times better .

deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports-staging main universe restricted multiverse

apt-get update then update beep-media-player, all that is fixed.


[BMP Plugins](http://www.sosdg.org/%7Elarne/w/Plugin_list)  <-- edit -- > If some plugins dont want to install, download beep media player's development package.[/QUOTE]
 Thanks /again/ for pointing me in the right direction.

---

### Post by Svictor on 2005-03-27
Haven't tried beep, but I had the same problems with small fonts in XMMS and solved them by installing xfonts-100dpi-transcoded ans xfonts-75dpi-transcoded. Then restarted X and XMMS display was OK.

---

