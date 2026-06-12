---
title: "added KDE from synaptic, how to remove all of it features???"
date: 2006-01-04
forum: Desktop Environments
---

### Post by syklitengutt on 2006-01-04
Hi... 
I wanted to add a little more action to my ubuntu and installed KDE.
Ifter trying it for like 5 min, I quickly desided no thnx.
I like gnome better.

How to remove KDE and all of the programs it installed??

---

### Post by Lord Illidan on 2006-01-04
```
sudo apt-get remove kubuntu-desktop
```

---

### Post by GeneralZod on 2006-01-04
Just 5 minutes? :(

Anyway, try this (simply doing sudo apt-get remove kubuntu-desktop doesn't actually work!)

[http://ubuntuforums.org/showthread.php?t=96048&highlight=uninstall+kde](http://ubuntuforums.org/showthread.php?t=96048&highlight=uninstall+kde)

---

### Post by Alpha_toxic on 2006-01-04
> 
```
sudo apt-get remove kubuntu-desktop 
```

I don't think this will do. This should only remove the package [COLOR="Red"]kubuntu-desktop[/COLOR], wich is only a meta-package (includes nothing, but depends on everything you need for KDE to run, so Synaptic installs a load of other packages with it.), so actually everything else will still be on your comp.

The best way to get rid of everything (at least the best I can think of...) is to search Synaptic's history (somewhere from within Synaptic), search for [COLOR="#ff0000"]kubuntu-desktop[/COLOR] and see the exact date/hour/minute it was installed. Then find all other packages installed at the same time and remove them.
This can be pretty anoying, as you have to do it one package at a time... perhaps copying their names and pasting them in a ```
sudo apt-get remove package1 package2 package3...
``` can make your life a bit easier.
Anyway this is equal to a complete rollback to the state before KDE was installed

---

### Post by syklitengutt on 2006-01-04
lol...
I dont mind the kde interface, but the all the programs I dont need.
And It was so... GLossy, and I dont know. Preffered Gnome....
Heres the list.... zzzz
> Installed the following packages:
akode (4:3.4.3-0ubuntu1)
akregator (4:3.4.3-0ubuntu3)
amor (4:3.4.3-0ubuntu2)
ark (4:3.4.3-0ubuntu1)
artsbuilder (4:3.4.3-0ubuntu1)
atlantik (4:3.4.3-0ubuntu1)
atlantikdesigner (4:3.4.3-0ubuntu1)
autoconf (2.59a-3)
automake1.4 (1:1.4-p6-9)
autotools-dev (20050422.1)
cervisia (4:3.4.3-0ubuntu1)
dcoprss (4:3.4.3-0ubuntu1)
dirmngr (0.9.1-2build1)
edict (2005.06.10-1)
enscript (1.6.4-7)
eyesapplet (4:3.4.3-0ubuntu2)
fifteenapplet (4:3.4.3-0ubuntu2)
gnupg-agent (1.9.15-6)
gnupg2 (1.9.15-6)
gpgsm (1.9.15-6)
imlib1 (1.9.14-16.2ubuntu4)
juk (4:3.4.3-0ubuntu1)
kaboodle (4:3.4.3-0ubuntu1)
kaddressbook (4:3.4.3-0ubuntu3)
kaddressbook-plugins (4:3.4.3-0ubuntu1)
kalarm (4:3.4.3-0ubuntu3)
kalzium (4:3.4.3-0ubuntu2)
kamera (4:3.4.3-0ubuntu2.1)
kandy (4:3.4.3-0ubuntu2)
kanjidic (2004.08.13-1)
kappfinder (4:3.4.3-0ubuntu6)
kapptemplate (4:3.4.3-0ubuntu1)
karm (4:3.4.3-0ubuntu3)
kasteroids (4:3.4.3-0ubuntu1)
kate (4:3.4.3-0ubuntu6)
kate-plugins (4:3.4.3-0ubuntu1)
katomic (4:3.4.3-0ubuntu1)
kaudiocreator (4:3.4.3-0ubuntu1)
kbabel (4:3.4.3-0ubuntu1)
kbackgammon (4:3.4.3-0ubuntu1)
kbattleship (4:3.4.3-0ubuntu1)
kblackbox (4:3.4.3-0ubuntu1)
kbounce (4:3.4.3-0ubuntu1)
kbruch (4:3.4.3-0ubuntu2)
kbstate (4:3.4.3-0ubuntu1)
kbugbuster (4:3.4.3-0ubuntu1)
kcachegrind (4:3.4.3-0ubuntu1)
kcalc (4:3.4.3-0ubuntu1)
kcharselect (4:3.4.3-0ubuntu1)
kcoloredit (4:3.4.3-0ubuntu2.1)
kcron (4:3.4.3-0ubuntu1)
kdat (4:3.4.3-0ubuntu1)
kde (5:44ubuntu2)
kde-amusements (5:44ubuntu2)
kde-core (5:44ubuntu2)
kdeaccessibility (4:3.4.3-0ubuntu1)
kdeaddons (4:3.4.3-0ubuntu1)
kdeaddons-kfile-plugins (4:3.4.3-0ubuntu1)
kdeadmin (4:3.4.3-0ubuntu1)
kdeadmin-kfile-plugins (4:3.4.3-0ubuntu1)
kdeartwork (4:3.4.3-0ubuntu1)
kdeartwork-emoticons (4:3.4.3-0ubuntu1)
kdeartwork-misc (4:3.4.3-0ubuntu1)
kdeartwork-style (4:3.4.3-0ubuntu1)
kdeartwork-theme-icon (4:3.4.3-0ubuntu1)
kdeartwork-theme-window (4:3.4.3-0ubuntu1)
kdebase (4:3.4.3-0ubuntu6)
kdebase-kio-plugins (4:3.4.3-0ubuntu6)
kdeedu (4:3.4.3-0ubuntu2)
kdeedu-data (4:3.4.3-0ubuntu2)
kdegames (4:3.4.3-0ubuntu1)
kdegames-card-data (4:3.4.3-0ubuntu1)
kdegraphics (4:3.4.3-0ubuntu2.1)
kdegraphics-kfile-plugins (4:3.4.3-0ubuntu2.1)
kdelibs (4:3.4.3-0ubuntu1)
kdelirc (4:3.4.3-0ubuntu1)
kdemultimedia (4:3.4.3-0ubuntu1)
kdemultimedia-kappfinder-data (4:3.4.3-0ubuntu1)
kdemultimedia-kfile-plugins (4:3.4.3-0ubuntu1)
kdemultimedia-kio-plugins (4:3.4.3-0ubuntu1)
kdenetwork (4:3.4.3-0ubuntu1)
kdenetwork-filesharing (4:3.4.3-0ubuntu1)
kdenetwork-kfile-plugins (4:3.4.3-0ubuntu1)
kdepasswd (4:3.4.3-0ubuntu6)
kdepim (4:3.4.3-0ubuntu2)
kdepim-kfile-plugins (4:3.4.3-0ubuntu2)
kdepim-kio-plugins (4:3.4.3-0ubuntu3)
kdepim-wizards (4:3.4.3-0ubuntu3)
kdeprint (4:3.4.3-0ubuntu6)
kdesdk (4:3.4.3-0ubuntu1)
kdesdk-kfile-plugins (4:3.4.3-0ubuntu1)
kdesdk-misc (4:3.4.3-0ubuntu1)
kdesdk-scripts (4:3.4.3-0ubuntu1)
kdesktop (4:3.4.3-0ubuntu6)
kdessh (4:3.4.3-0ubuntu1)
kdetoys (4:3.4.3-0ubuntu2)
kdeutils (4:3.4.3-0ubuntu1)
kdevelop3 (4:3.2.3-0ubuntu1)
kdevelop3-data (4:3.2.3-0ubuntu1)
kdevelop3-plugins (4:3.2.3-0ubuntu1)
kdewallpapers (4:3.4.3-0ubuntu1)
kdewebdev (4:3.4.3-0ubuntu2)
kdf (4:3.4.3-0ubuntu1)
kdict (4:3.4.3-0ubuntu1)
kdvi (4:3.4.3-0ubuntu2.1)
kedit (4:3.4.3-0ubuntu1)
keduca (4:3.4.3-0ubuntu2)
kenolaba (4:3.4.3-0ubuntu1)
kfax (4:3.4.3-0ubuntu2.1)
kfilereplace (4:3.4.3-0ubuntu2)
kfind (4:3.4.3-0ubuntu6)
kfloppy (4:3.4.3-0ubuntu1)
kfouleggs (4:3.4.3-0ubuntu1)
kgamma (4:3.4.3-0ubuntu2.1)
kget (4:3.4.3-0ubuntu1)
kghostview (4:3.4.3-0ubuntu2.1)
kgoldrunner (4:3.4.3-0ubuntu1)
kgpg (4:3.4.3-0ubuntu1)
khangman (4:3.4.3-0ubuntu2)
khelpcenter (4:3.4.3-0ubuntu6)
khexedit (4:3.4.3-0ubuntu1)
kicker (4:3.4.3-0ubuntu6)
kicker-applets (4:3.4.3-0ubuntu1)
kiconedit (4:3.4.3-0ubuntu2.1)
kig (4:3.4.3-0ubuntu2)
kimagemapeditor (4:3.4.3-0ubuntu2)
kitchensync (4:3.4.3-0ubuntu3)
kiten (4:3.4.3-0ubuntu2)
kjots (4:3.4.3-0ubuntu1)
kjumpingcube (4:3.4.3-0ubuntu1)
klaptopdaemon (4:3.4.3-0ubuntu1)
klatin (4:3.4.3-0ubuntu2)
kleopatra (4:3.4.3-0ubuntu2)
klettres (4:3.4.3-0ubuntu2)
klettres-data (4:3.4.3-0ubuntu2)
klickety (4:3.4.3-0ubuntu1)
klines (4:3.4.3-0ubuntu1)
klinkstatus (4:3.4.3-0ubuntu2)
klipper (4:3.4.3-0ubuntu6)
kmag (4:3.4.3-0ubuntu1)
kmahjongg (4:3.4.3-0ubuntu1)
kmail (4:3.4.3-0ubuntu3)
kmailcvt (4:3.4.3-0ubuntu2)
kmenuedit (4:3.4.3-0ubuntu6)
kmessedwords (4:3.4.3-0ubuntu2)
kmid (4:3.4.3-0ubuntu1)
kmilo (4:3.4.3-0ubuntu1)
kmines (4:3.4.3-0ubuntu1)
kmix (4:3.4.3-0ubuntu1)
kmoon (4:3.4.3-0ubuntu2)
kmousetool (4:3.4.3-0ubuntu1)
kmouth (4:3.4.3-0ubuntu1)
kmplot (4:3.4.3-0ubuntu2)
kmrml (4:3.4.3-0ubuntu2.1)
kmtrace (4:3.4.3-0ubuntu1)
knewsticker (4:3.4.3-0ubuntu1)
knewsticker-scripts (4:3.4.3-0ubuntu1)
knode (4:3.4.3-0ubuntu2)
knotes (4:3.4.3-0ubuntu3)
kodo (4:3.4.3-0ubuntu2)
kolf (4:3.4.3-0ubuntu1)
kolourpaint (4:3.4.3-0ubuntu2.1)
kommander (4:3.4.3-0ubuntu2)
kompare (4:3.4.3-0ubuntu1)
konq-plugins (4:3.4.3-0ubuntu1)
konqueror (4:3.4.3-0ubuntu6)
konqueror-nsplugins (4:3.4.3-0ubuntu6)
konquest (4:3.4.3-0ubuntu1)
konsole (4:3.4.3-0ubuntu6)
konsolekalendar (4:3.4.3-0ubuntu2)
kontact (4:3.4.3-0ubuntu3)
kooka (4:3.4.3-0ubuntu2.1)
kopete (4:3.4.3-0ubuntu1)
korganizer (4:3.4.3-0ubuntu3)
korn (4:3.4.3-0ubuntu2)
kpackage (4:3.4.3-0ubuntu1)
kpager (4:3.4.3-0ubuntu6)
kpat (4:3.4.3-0ubuntu1)
kpdf (4:3.4.3-0ubuntu2.1)
kpercentage (4:3.4.3-0ubuntu2)
kpersonalizer (4:3.4.3-0ubuntu6)
kpf (4:3.4.3-0ubuntu1)
kpilot (4:3.4.3-0ubuntu3)
kpoker (4:3.4.3-0ubuntu1)
kpovmodeler (4:3.4.3-0ubuntu2.1)
kppp (4:3.4.3-0ubuntu1)
krdc (4:3.4.3-0ubuntu1)
krec (4:3.4.3-0ubuntu1)
kregexpeditor (4:3.4.3-0ubuntu1)
kreversi (4:3.4.3-0ubuntu1)
krfb (4:3.4.3-0ubuntu1)
kruler (4:3.4.3-0ubuntu2.1)
ksame (4:3.4.3-0ubuntu1)
ksayit (4:3.4.3-0ubuntu1)
kscd (4:3.4.3-0ubuntu1)
kscreensaver (4:3.4.3-0ubuntu1)
kscreensaver-xsavers (4:3.4.3-0ubuntu1)
kshisen (4:3.4.3-0ubuntu1)
ksig (4:3.4.3-0ubuntu1)
ksim (4:3.4.3-0ubuntu1)
ksirc (4:3.4.3-0ubuntu1)
ksirtet (4:3.4.3-0ubuntu1)
ksmiletris (4:3.4.3-0ubuntu1)
ksmserver (4:3.4.3-0ubuntu6)
ksnake (4:3.4.3-0ubuntu1)
ksnapshot (4:3.4.3-0ubuntu2.1)
ksokoban (4:3.4.3-0ubuntu1)
kspaceduel (4:3.4.3-0ubuntu1)
ksplash (4:3.4.3-0ubuntu6)
kspy (4:3.4.3-0ubuntu1)
kstars (4:3.4.3-0ubuntu2)
kstars-data (4:3.4.3-0ubuntu2)
ksvg (4:3.4.3-0ubuntu2.1)
ksync (4:3.4.3-0ubuntu3)
ksysguard (4:3.4.3-0ubuntu6)
ksysguardd (4:3.4.3-0ubuntu6)
ksysv (4:3.4.3-0ubuntu1)
kteatime (4:3.4.3-0ubuntu2)
ktimer (4:3.4.3-0ubuntu1)
ktip (4:3.4.3-0ubuntu6)
ktnef (4:3.4.3-0ubuntu2)
ktouch (4:3.4.3-0ubuntu2)
ktron (4:3.4.3-0ubuntu1)
kttsd (4:3.4.3-0ubuntu1)
ktuberling (4:3.4.3-0ubuntu1)
kturtle (4:3.4.3-0ubuntu2)
ktux (4:3.4.3-0ubuntu2)
kuickshow (4:3.4.3-0ubuntu2.1)
kuiviewer (4:3.4.3-0ubuntu1)
kuser (4:3.4.3-0ubuntu1)
kverbos (4:3.4.3-0ubuntu2)
kview (4:3.4.3-0ubuntu2.1)
kviewshell (4:3.4.3-0ubuntu2.1)
kvoctrain (4:3.4.3-0ubuntu2)
kwalletmanager (4:3.4.3-0ubuntu1)
kweather (4:3.4.3-0ubuntu2)
kwifimanager (4:3.4.3-0ubuntu1)
kwin (4:3.4.3-0ubuntu6)
kwin4 (4:3.4.3-0ubuntu1)
kwordquiz (4:3.4.3-0ubuntu2)
kworldclock (4:3.4.3-0ubuntu2)
kxsldbg (4:3.4.3-0ubuntu2)
libapr0 (2.0.54-5ubuntu3)
libarts1-audiofile (4:3.4.3-0ubuntu1)
libarts1-mpeglib (4:3.4.3-0ubuntu1)
libarts1-xine (4:3.4.3-0ubuntu1)
libboost-python1.33.0 (1.32.0+1.33.0-cvs20050727-1ubuntu1)
libconvert-binhex-perl (1.119-2)
libcvsservice0 (4:3.4.3-0ubuntu1)
libfinance-quote-perl (1.08-1)
libgadu3 (1:1.5+20050411-2ubuntu3)
libgpgme11 (1.0.2-1build1)
libhtml-parser-perl (3.45-2)
libhtml-tableextract-perl (1.08-1)
libhtml-tagset-perl (3.04-1)
libhtml-tree-perl (3.18-1)
libio-stringy-perl (2.110-1)
libjpeg-progs (6b-10)
libkcal2a (4:3.4.3-0ubuntu3)
libkcddb1 (4:3.4.3-0ubuntu1)
libkdeedu1 (4:3.4.3-0ubuntu2)
libkdegames1 (4:3.4.3-0ubuntu1)
libkdepim1 (4:3.4.3-0ubuntu3)
libkgantt0 (4:3.4.3-0ubuntu2)
libkiten1 (4:3.4.3-0ubuntu2)
libkleopatra0a (4:3.4.3-0ubuntu3)
libkonq4 (4:3.4.3-0ubuntu6)
libkpimexchange1 (4:3.4.3-0ubuntu3)
libkpimidentities1 (4:3.4.3-0ubuntu3)
libksba8 (0.9.9-2)
libkscan1 (4:3.4.3-0ubuntu2.1)
libksieve0 (4:3.4.3-0ubuntu3)
libktnef1 (4:3.4.3-0ubuntu3)
libmailtools-perl (1.62-1)
libmal1 (0.40-3)
libmime-perl (5.417-1)
libmimelib1a (4:3.4.3-0ubuntu3)
libnews-nntpclient-perl (0.37-5)
libopenct1 (0.6.5-1)
libopensc1 (0.9.6-1)
libpcsclite1 (1.2.9-beta7-5)
libpth2 (2.0.1-2)
librss1 (4:3.4.3-0ubuntu1)
libsensors3 (1:2.9.1-4ubuntu3)
libsvn0 (1.2.0-1ubuntu1)
libtidy0 (20050415-1)
libtiff-tools (3.7.3-1ubuntu1)
libtimedate-perl (1.1600-4)
libtunepimp-bin (0.3.0-2ubuntu7)
liburi-perl (1.35-1)
libwww-perl (5.803-4)
libxcomposite1 (1:0.2.0-3)
lskat (4:3.4.3-0ubuntu1)
mpeglib (4:3.4.3-0ubuntu1)
networkstatus (4:3.4.3-0ubuntu2)
noatun (4:3.4.3-0ubuntu1)
noatun-plugins (4:3.4.3-0ubuntu1)
openssh-server (1:4.1p1-7ubuntu4)
pinentry-qt (0.7.2-1build1)
poster (20020830-2)
poxml (4:3.4.3-0ubuntu1)
psutils (1.17-17)
quanta (4:3.4.3-0ubuntu2)
quanta-data (4:3.4.3-0ubuntu2)
secpolicy (4:3.4.3-0ubuntu1)
ssh (1:4.1p1-7ubuntu4)
tidy (20050415-1)
umbrello (4:3.4.3-0ubuntu1)
vim-gtk (1:6.3-078+1ubuntu3)
vimpart (4:3.4.3-0ubuntu1)


That aint a small list.

---

### Post by Alpha_toxic on 2006-01-04
LOL I didn't realise the list would be so huge!!! [COLOR="Red"]xubuntu-desktop[/COLOR] installed much less stuff when I tried it...
If you haven't given up yet, you can delete everything that is in brackets from the list. Then it shoud look like this
```

akode
akregator
amor
ark
artsbuilder
.
.
.

```
Then copy/paste it in 
```

sudo apt-get remove <paste here>

```
I really hope that this is NOT the best way to do this. Or I'll never install anything bigger than 20 packages...

---

### Post by syklitengutt on 2006-01-04
im doing what you said...
Just taking a brake.

Is it possible to make a script or something so that I can save this later.

Just add it in the ubuntuforums, in case someone does the same thing themselve and want to remove it again.

And to add a stoopid question to it all.
How do I make a shortcut to /mnt/hdb (my new hdd) to add on my desctop?
its mounted all the time... I just want a shortcut that I can click to get into the folder troug nautilus.
I was thinking about a starter or something

---

### Post by Lord Illidan on 2006-01-04
Sorry for the mishint, i thought it would work, but it doesn't...
Still, you should have sticked around... KDE's power is awesome, but then, that's why we have choice!

---

### Post by syklitengutt on 2006-01-04
perhaps kde is good.... But now im used to gnome...
Kde reminds me a little of windows... 
sorry to say that....

---

### Post by GrumpyBob on 2006-01-04
[QUOTE=GeneralZod]Just 5 minutes? :(

Anyway, try this (simply doing sudo apt-get remove kubuntu-desktop doesn't actually work!)

[http://ubuntuforums.org/showthread.php?t=96048&highlight=uninstall+kde](http://ubuntuforums.org/showthread.php?t=96048&highlight=uninstall+kde)[/QUOTE]


I've got both KDE and Gnome on a Ubuntu box here, but don't use KDE as I prefer Gnome.  KDE is just too busy for my tired head.  However, I've left it there for the time being so I can go back and have another go later on!  I would say that 5 minutes was quite enough for me as well.

Robert

---

### Post by conor on 2006-01-04
I tried KDE and liked it for a while, I had all of the panels customized so that the menus and launchers appered exactly as they did in ubuntu-gnome.  it just takes a little getting used to.  But I had to switch back to Gnome bacause my Laptop has really low ram and KDE is more resource intensive.  I had an option that you could use to get rid of KDE...   

install the package debfoster and run it from the terminal.  
it will say kubuntu-desktop is keeping the following packages installed .........
hit 'p' for prune and it will uninstall all of the packages.  The only problem is that some of the kubuntu-desktop pakages are neccesary to run ubuntu (some of the libs) so you may need to install ubuntu desktop to get them back, or so I would assume.

---

### Post by conor on 2006-01-04
Oh wait, did you follow GeneralZod's link?  

> ```
sudo apt-get remove --purge adept akregator amarok amarok-gstreamer ark arts debtags enscript gtk2-engines-gtk-qt gwenview imagemagick ivman kaddressbook kaffeine  kaffeine-gstreamer kamera kappfinder karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin libgadu3 libgpgme11 libjpeg-progs libkcal2a libkcddb1 libkdepim1 libkipi0 libkleopatra0a libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1a libopenobex-1.0-0 libpythonize0 libsensors3 libtdb1 openoffice.org2-kde poster psutils python-kde3 python-opengl python2.4-dev python2.4-kde3 python2.4-opengl python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex sanekonsole speedcrunch ttf-dejavu xlibs
```

Its all right there.  Never mind copying and pasting everything from your list, its already been done by aysiu.

---

### Post by Alpha_toxic on 2006-01-04
Aysiu did a great job, but this was on his box...
I can bet that there are differences in the packages that he installed and the ones that syklitengutt installed. Perhaps he (either one of them) had already installed some apps that use some of KDE's librarys and stuff, brute-force uninstalling them Aysiu's way might just work, but also can get you in some realy deep shit if it's not Aysiu's comp :( (I mean that in Synaptic you get enough warnings that you are also removing packages dependant on your initial list and you can see what packages you might not want to remove, but in cmd line you just press enter and they are all gone...)

And about the script that syklitengutt wants:
I think it would be best if it was included in Synaptic. An easy way to remove/reinstall stuff from the history would be best. Sth like choosing an entry from the history and having the same options as when right-clicked on a package in the main Synaptic window. This will solve all uor problems (allmost) :) . Maybe someone should fill a bug report or sth...

---

### Post by leech on 2006-01-04
Actually removing a lot of packages like that from the command line won't just remove them all without any input.  You have to confirm it first of all, and second of all, it will actually say "Additional packages will be REMOVED" as well.  

I do agree with a lot of the opinions here, 5 minutes with KDE and back to gnome... :D

Leech

---

