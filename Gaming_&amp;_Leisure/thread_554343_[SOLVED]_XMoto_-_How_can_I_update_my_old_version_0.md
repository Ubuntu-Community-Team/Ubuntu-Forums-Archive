---
title: "[SOLVED] XMoto - How can I update my old version 0.2.4-2 to 0.3.3 ?"
date: 2007-09-18
forum: Gaming &amp; Leisure
---

### Post by MozartlovesUbun2 on 2007-09-18
[http://xmoto.sourceforge.net/](http://xmoto.sourceforge.net/)   is providing the new Xmoto 0.3.3
but when I go to Synaptics Package Manager it just still offers me the old 0.2.4-2 version!

So please how do I update? :confused:

---

### Post by misfitpierce on 2007-09-18
[http://www.getdeb.net/release.php?id=1350](http://www.getdeb.net/release.php?id=1350)

Just download the package from getdeb and install... It'll update it.

---

### Post by MozartlovesUbun2 on 2007-09-18
> **misfitpierce said:**
> [http://www.getdeb.net/release.php?id=1350](http://www.getdeb.net/release.php?id=1350)

Just download the package from getdeb and install... It'll update it.

hmm, I did, no luck

I downloaded the xmoto_0.3.3-0~getdeb1_i386.deb file which is only 1.0MB!

if I double click it, it opens in "Package Installer - xmoto"

it says

"Error: Dependency is not satisfiable: xmoto-data"

ask I please ask for a little step by step instructions, which file should I download and how to I run it to update my old Xmoto

thanks

---

### Post by misfitpierce on 2007-09-18
Ok try this...

Go to system - admin - synaptic package manager...
Search for xmoto
Click box next to it and select remove completely
Then wait for it to finish and close synaptic package manager
Now download new .deb for xmoto.
Comes in 2 packages usually on a lot of games.
[http://www.getdeb.net/download.php?release=1350&fpos=1](http://www.getdeb.net/download.php?release=1350&fpos=1) - xmoto-data

[http://www.getdeb.net/download.php?release=1350&fpos=0](http://www.getdeb.net/download.php?release=1350&fpos=0) - xmoto

Always install data package first then the game or software. Try that and let me know how it goes.

---

### Post by MozartlovesUbun2 on 2007-09-18
thank you, that worked

one of your link seems to be broken, so I got the two packages from here

[http://www.getdeb.net/release.php?id=1350](http://www.getdeb.net/release.php?id=1350)

uninstalled the other 2 old ones and put the new ones on

great now the game works and doesn't crash my PC when I exit
===============================

looking at their website

[http://xmoto.sourceforge.net/](http://xmoto.sourceforge.net/)

they have another newer package "28/08/2007 - Inksmoto Level Editor (svg2lvl) 0.4.1 released"

inksmoto-0.4.1.tar.gz	Plateform independant (GNU/Linux, MacOSX, Windows, ...)

Is that a newer update?

do I now always have to manually update, will Synaptic not work?

---

### Post by MozartlovesUbun2 on 2007-09-18
[http://xmoto.sourceforge.net/](http://xmoto.sourceforge.net/)

there a level editor, great

didn't know there was one

has anyone used this before?

so how do I install it :)

---

### Post by Perfect Storm on 2007-09-18
[http://gaming.gwos.org/doku.php/guides:guides](http://gaming.gwos.org/doku.php/guides:guides) try this guide.

> do I now always have to manually update, will Synaptic not work?

Well, the .deb will properly overwrite it, if you one day install a .deb package. Or if you install it in diffrent location you'll end up with duplicates.

---

### Post by MozartlovesUbun2 on 2007-09-19
> **Artificial Intelligence said:**
> [http://gaming.gwos.org/doku.php/guides:guides](http://gaming.gwos.org/doku.php/guides:guides) try this guide.



Well, the .deb will properly overwrite it, if you one day install a .deb package. Or if you install it in diffrent location you'll end up with duplicates.

ok sorry for this lame question, um so who is responsible taking care of the Synaptics Updates, do they usually update the games on a lower priority :)

so do I have to manually always go look for the latest updates for my games?

---

### Post by Perfect Storm on 2007-09-19
If you installed the game manually, synaptic won't detect it. So no worry.

---

### Post by MozartlovesUbun2 on 2007-09-20
> **Artificial Intelligence said:**
> If you installed the game manually, synaptic won't detect it. So no worry.

Yes I had to manually uninstall the old one and put the new one in it works great, thanks, though riding that bike is extremely hard and  very fustrating, hmm I'ld like to make a few levels of my own, did try to get that plugin for inkscape, but couldn't get it installed.

---

### Post by Perfect Storm on 2007-09-20
Give me some days and I'll write a guide for the inkscape plugin.

---

### Post by MozartlovesUbun2 on 2007-09-21
> **Artificial Intelligence said:**
> Give me some days and I'll write a guide for the inkscape plugin.

A big Thank You once more Artificial Intelligence :)

---

### Post by Perfect Storm on 2007-09-21
I have wrote the "skeleton" of it, but not yest posted in a guide, here's the rough;

```

sudo aptitude update && sudo aptitude upgrade
sudo aptitude install inkscape python-tk python-xml

cd ~/Desktop
tar zxfv inksmoto-0.4.1.tar.gz
cd inksmoto-0.4.1
rm -rf ~/.inkscape/extensions/
mkdir -p ~/.inkscape/extensions/
cp -f * ~/.inkscape/extensions/

```

Then start inkscape.

---

### Post by MozartlovesUbun2 on 2007-09-21
> **Artificial Intelligence said:**
> I have wrote the "skeleton" of it, but not yest posted in a guide, here's the rough;

```

sudo aptitude update && sudo aptitude upgrade
sudo aptitude install inkscape python-tk python-xml

cd ~/Desktop
tar zxfv inksmoto-0.4.1.tar.gz
cd inksmoto-0.4.1
rm -rf ~/.inkscape/extensions/
mkdir -p ~/.inkscape/extensions/
cp -f * ~/.inkscape/extensions/

```

Then start inkscape.

Merci Beacoup, the children were getting ever so impatient, so gonna be some serious Xmoto map making sessions now :)

I just wished that if dude riding the bike didn't fall off so easily, gets very fustrating in most of the levels, which lowers the fun factor.

nice things are the bouncy bike (should be more breakable) the sounds perfect, like snapping his neck, should be a bit louder

all in all i guess the games still being developed so looking forward for the first finished version.

thx A.I.

---

### Post by Perfect Storm on 2007-09-21
Try check over at UGA for the latest news. There's a game your kids properly would like.

---

