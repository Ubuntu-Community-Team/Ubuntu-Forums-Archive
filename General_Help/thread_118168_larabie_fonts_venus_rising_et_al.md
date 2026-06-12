---
title: "larabie fonts: venus rising et al"
date: 2006-01-16
forum: General Help
---

### Post by Gowator on 2006-01-16
I just had to reinstall after adept screwed my system (or more accurately I just said YES) and I can't work out where I got some of the fonts from.... 

I used to have one called venus rising and another forgotten futurist ... both of which I used and need ...

synaptic acan't find them in any package on the sources I have installed. (Breezy inclubing universe and multiverse) does anyone know where they can be found ...

---

### Post by Gowator on 2006-01-17
just a little /bump ....

anyone any ideas

---

### Post by Miguel on 2006-01-17
I guess you have already installed msttcorefont, haven't you? 

If you have, the only chance is that you installed the other fonts from either a windows partition using defoma or similar. Anyway, you could have a look at [gnome-look.org](gnome-look.org). They have a fonts section.

---

### Post by Gowator on 2006-01-17
[QUOTE=Miguel]I guess you have already installed msttcorefont, haven't you? 

If you have, the only chance is that you installed the other fonts from either a windows partition using defoma or similar. Anyway, you could have a look at [gnome-look.org](gnome-look.org). They have a fonts section.[/QUOTE]
Yep already did MS core fonts (thx arnieboy) and I searched all of the packagesin my repo's so I think I must have had them from a different repo which I have forgotten about... probably found it for some other app and when looking for fonts ended up finding them... but I even tried apt-get.org and no luck though they could be called sometihng different in the package!

---

### Post by Miguel on 2006-01-17
I've done some searching and, well, when I was going to tell you to download the fonts and do it the tough way (you know, extracting the files, putting them in a system wide folder, create a config file and then register the fonts with defoma)... I just found some good news.

The larabie fonts are available as a debian package. This made me think that maybe, just maybe, they were available in ubuntu (in the worst case, a dpkg -i wouldn't hurt). And, voilá:

```
miguel@lcpybm:~$ apt-cache search larabie
ttf-larabie-deco - Decorative fonts from www.larabiefonts.com
ttf-larabie-straight - Straight fonts from www.larabiefonts.com
ttf-larabie-uncommon - Special decorative fonts from www.larabiefonts.com

```

```
miguel@lcpybm:~$ apt-cache show ttf-larabie-deco
Package: ttf-larabie-deco
Priority: optional
Section: multiverse/x11
Installed-Size: 7844
Maintainer: Erich Schubert <erich@debian.org>
Architecture: all
Source: ttf-larabie
Version: 20011216-3ubuntu1
Depends: xutils
Filename: pool/multiverse/t/ttf-larabie/ttf-larabie-deco_20011216-3ubuntu1_all.deb
Size: 3066014
MD5sum: ec440b11dfd4f32137d93176e78389af
Description: Decorative fonts from www.larabiefonts.com
 Decorative freeware TrueType fonts from Ray Larabie.
 This package contains the "decorative" ones of his fonts,
 which are great for headlines and other decorations.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

My take is that all three packages ara available in multiverse. What's more, I have only activated backports (if you are wondering). Now I will laugh if the two fonts you are looking for aren't in these three packages.

---

### Post by Miguel on 2006-01-17
OK, I have installed all three packages and I can confirm that the fonts you were looking for are indeed inside. But don't ask me in wich one of those 21MB packages are ;) Just joking,

Miguel

---

### Post by Gowator on 2006-01-18
[QUOTE=Miguel]OK, I have installed all three packages and I can confirm that the fonts you were looking for are indeed inside. But don't ask me in wich one of those 21MB packages are ;) Just joking,

Miguel[/QUOTE]
OK This is cool... thanks :D
I guess I will go with all three too since they are some nice fonts ....
This is just i time I was starting to think I would have to redo the flier I made using these fonts ...

:p

---

### Post by Gowator on 2006-01-18
Aggghhhh ... you were SO right.
I had these font installed all the time and I just kept checking in OpenOffice ... but not seeing them.  I checked the installed files and they were in the right directory and closing OO (including quick start) was needed to let OO see them ...

I got myself into such a panic .... I couldn't see venus rising for the sun !

---

