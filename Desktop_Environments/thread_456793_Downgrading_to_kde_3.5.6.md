---
title: "Downgrading to kde 3.5.6"
date: 2007-05-28
forum: Desktop Environments
---

### Post by dumas33 on 2007-05-28
Few days ago I upgradet my Kubuntu 7.04 to kde 3.5.7

I was hoping the solved some issues whit kitchensync puting it to opensync engine. Unfortunetely I was wrong. 
Now I want to donwgrade to officially supported 3.5.6 Any Ideas how to do that?

---

### Post by dumas33 on 2007-05-29
So, no idea how to downgrade? :(

---

### Post by g8m on 2007-05-29
google apt downgrade software

Downgrading From Unreleased to Released

You can downgrade packages on your machine. This means that if you have a testing or unstable package installed, and you don't want it any more, you can downgrade the package to the latest stable version.

Before being able to downgrade, you must make an entry in your /etc/apt/preferences file. The entry looks like the following:

Package: php4
Pin: release a=stable
Priority: 1001

Once you make this entry you can run the following command to downgrade a package:

prompt$ apt-get update

---

### Post by dumas33 on 2007-06-01
There are no  /etc/apt/preferences in kubuntu 7,04.
Any more idea?

---

### Post by g8m on 2007-06-01
create it?

man apt-get sayz:

/etc/apt/preferences
Version preferences file. This is where you should specify "pinning"

So if its not there:
  cd /etc/apt
  sudo touch preferences
  sudo kate preferences

et voila it;s there. Ouch time can begin.

---

### Post by Robin T Cox on 2007-06-01
See:

[http://seerofsouls.com/wiki/How-Tos/DowngradingKDE]("http://seerofsouls.com/wiki/How-Tos/DowngradingKDE")

You will need to downgrade to the Edgy version of KDE 3.5.6, so your /etc/apt/sources.list entry will be:

> deb [http://kubuntu.org/packages/kde-356/](http://kubuntu.org/packages/kde-356/) edgy main

---

### Post by neptho on 2007-07-06
What I did was to remove the 3.5.7 repos from my /etc/apt/sources.list, then do an update to remove the indexes.

I proceeded to get a list of the most common kde applications, and came up with this list:

```
kdepim blinken korn kmoon ksim kdessh kanagram libpth20 kleopatra ktux
  klettres dirmngr kdepim-kfile-plugins libkiten1 liburi-perl konsolekalendar
  klatin kfloppy kstars ttf-dustin kbruch libhtml-parser-perl libpisock9
  keduca kandy kdeedu-data kmplot kweather kalzium ksayit kmouth kalarm
  kworldclock kalzium-data kdewebdev amor ktouch ktnef khexedit
  kdeaccessibility kvoctrain kdetoys kimagemapeditor kwordquiz ttf-sjfonts
  kdenetwork kttsd dcoprss klettres-data libksba8 kig gnupg-agent
  fifteenapplet kstars-data edict kdeutils khangman libindex0 kanjidic kpilot
  libmal1 libkdeedu3 libkgantt0 knewsticker libhtml-tree-perl kiten eyesapplet
  libwww-perl indi kdeedu kdelirc kpercentage superkaramba pinentry-qt
  libhtml-tagset-perl libboost-python1.33.1 gpgsm gnupg2 kdepim-wizards
  kturtle ktimer kverbos kodo kde kde-amusements kde-core kubuntu-desktop
```

So I ran (without the returns, of course):

```
apt-get remove kdepim blinken korn kmoon ksim kdessh kanagram libpth20 kleopatra ktux
  klettres dirmngr kdepim-kfile-plugins libkiten1 liburi-perl konsolekalendar
  klatin kfloppy kstars ttf-dustin kbruch libhtml-parser-perl libpisock9
  keduca kandy kdeedu-data kmplot kweather kalzium ksayit kmouth kalarm
  kworldclock kalzium-data kdewebdev amor ktouch ktnef khexedit
  kdeaccessibility kvoctrain kdetoys kimagemapeditor kwordquiz ttf-sjfonts
  kdenetwork kttsd dcoprss klettres-data libksba8 kig gnupg-agent
  fifteenapplet kstars-data edict kdeutils khangman libindex0 kanjidic kpilot
  libmal1 libkdeedu3 libkgantt0 knewsticker libhtml-tree-perl kiten eyesapplet
  libwww-perl indi kdeedu kdelirc kpercentage superkaramba pinentry-qt
  libhtml-tagset-perl libboost-python1.33.1 gpgsm gnupg2 kdepim-wizards
  kturtle ktimer kverbos kodo  kde kde-amusements kde-core kubuntu-desktop
```

Followed by (without the returns, of course):

```
apt-get install kdepim blinken korn kmoon ksim kdessh kanagram libpth20 kleopatra ktux
  klettres dirmngr kdepim-kfile-plugins libkiten1 liburi-perl konsolekalendar
  klatin kfloppy kstars ttf-dustin kbruch libhtml-parser-perl libpisock9
  keduca kandy kdeedu-data kmplot kweather kalzium ksayit kmouth kalarm
  kworldclock kalzium-data kdewebdev amor ktouch ktnef khexedit
  kdeaccessibility kvoctrain kdetoys kimagemapeditor kwordquiz ttf-sjfonts
  kdenetwork kttsd dcoprss klettres-data libksba8 kig gnupg-agent
  fifteenapplet kstars-data edict kdeutils khangman libindex0 kanjidic kpilot
  libmal1 libkdeedu3 libkgantt0 knewsticker libhtml-tree-perl kiten eyesapplet
  libwww-perl indi kdeedu kdelirc kpercentage superkaramba pinentry-qt
  libhtml-tagset-perl libboost-python1.33.1 gpgsm gnupg2 kdepim-wizards
  kturtle ktimer kverbos kodo  kde kde-amusements kde-core kubuntu-desktop
```

..and I was back to Feisty Kubuntu 3.5.6, with minimal fuss, and didn't lose any of my personal effects.. that I know of.  Playing dirty, I did this from within 3.5.7, logged out, restarted my X server from kdm, and logged right back into 3.5.6.

---

