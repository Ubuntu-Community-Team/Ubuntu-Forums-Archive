---
title: "KDE's Stability."
date: 2009-11-20
forum: Desktop Environments
---

### Post by Roasted on 2009-11-20
I don't mean to stir up the pot here but I just have a really sincere question. How stable is KDE 4.3? Reason I ask is I decided to check out Kubuntu based on a lot of good praise that KDE got on this forum. I've been running it full time on my spare computer here for a few days. Previously I hadn't used it much at all, but last night I used the computer 2 hours straight, and Plasma crashed 3 times in that time frame by doing simple things, such as adding a widget to the panel, closing Amarok from the system tray, and opening Firefox.

To me, this is a severe red flag, being I've been a gnome user for 4 years and I never recall having a crash. Then I fire up KDE and - 3 times in one night..? 

What is  Plasma, exactly, and what relationship does it have with KDE in general?

---

### Post by lovinglinux on 2009-11-20
Plasma crashes for me when trying to add the Microblogging widget. I get a black screen. I think everything is running in the background, but I have no desktop.

It also crashes if I click the "Kickoff" menu just after login in, while other panel widgets and the tray are still loading. In this case, I don't get a black screen, plasma simply freezes.

Other than that, it's pretty much stable.


> From [http://en.wikipedia.org/wiki/Plasma_%28KDE%29](http://en.wikipedia.org/wiki/Plasma_%28KDE%29)

Plasma, part of KDE 4, is a fundamental rewrite of several desktop interaction technologies included in the KDE desktop environment for Linux and other Unix-like systems, focusing on eyecandy and special graphical effects. It most notably replaces the previous KDesktop shell, Kicker taskbar and SuperKaramba widget engine used in the KDE 3 series with a unified workspace for KDE 4. Plasma also provides a resolution-independent interface for KDE, making the desktop look identical almost regardless of screen size or resolution. Plasma's applets are collectively called plasmoids, but range from informative widgets to mini-applications like calculators and dictionaries. An important feature of Plasma is that there is no longer a distinction between panels (like the taskbar), desktop icons, and widgets; they are created the same way.

---

### Post by Roasted on 2009-11-20
Wow. That's a bummer. From all of the praise I was hearing the last thing I expected was 3 crashes in 1 night. *shrug*

EDIT - to be fair, I did install Ubuntu and then Kubuntu desktop on top of it. I also know this computer has weird graphics issues (HP dx2200, integrated video). Sometimes when I boot to an Ubuntu LiveCD, it'll show the Ubuntu splash screen in 3 different offset locations on my screen. It still boots, but looks weird.

So to be fair I should make those notations aware. I plan to install a native Kubuntu install on that machine later tonight. At the time I couldn't get the Kubuntu CD I had to work (ISO had an error). I'll give it another shot. I keep reading more and more people are speaking highly of KDE 4.3... so I gotta be fair and try it again in a more sensible environment with the native live cd.

---

### Post by Zorael on 2009-11-20
If DrKonqi starts (the KDE crash handler) when plasma crashes, consider sending the generated report to bugs.kde.org. Perhaps it's an unfortunate mismatch with your hardware, if you're having other graphics issues.

4.3.3 is also available from the Kubuntu PPAs; if it's a known issue, perhaps it has been fixed.

[ppa:kubuntu-ppa/ppa](https://launchpad.net/~kubuntu-ppa/+archive/ppa)
[ppa:kubuntu-ppa/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports)

Remember, unreported bugs can only be fixed by accident.

---

### Post by captaincrook on 2009-11-20
My only issue is that Plasma likes to chomp on my memory (~200MB) along with Xorg (200+), so I think something's connected there. Anyways, if you really want some KDE love, try OpenSUSE's latest release in a VM program.

---

### Post by Melcar on 2009-11-20
OpenSuse or even Fedora have better KDE desktops than Ubuntu.

---

### Post by Roasted on 2009-11-20
Yeahhhhh but I'm a sucker for debian. :(

EDIT - just installed Fedora KDE on my spare rig, on top of Kubuntu. What's the difference? How is Fedora's KDE better than Kubuntu's? Looks and operates the exact same way best I can tell.

---

### Post by captaincrook on 2009-11-20
> **Roasted said:**
> Yeahhhhh but I'm a sucker for debian. :(

EDIT - just installed Fedora KDE on my spare rig, on top of Kubuntu. What's the difference? How is Fedora's KDE better than Kubuntu's? Looks and operates the exact same way best I can tell.

The implementation is better as is the integration. If you don't mind living on the edge, try giving Sidux a try. That's also a good KDE distro based on Debian Sid, although it is a "rolling release" due to the Sid base.

---

### Post by Roasted on 2009-11-20
KDE on Kubuntu seems much more stable than KDE on Ubuntu + KDE from synaptic. It just felt like the system in general was sluggish when I did that.

I definitely like KDE on Kubuntu even more now that I did a fresh install properly. This may be beyond what the user sees but, like I said, I tinkered with Fedora KDE more and more and comparing it to Kubuntu... I just don't see a difference. *shrug*

---

### Post by Roasted on 2009-11-21
EDIT - I'm an idiot. Deleted.

---

### Post by gerowen on 2009-11-21
Just tried KDE4, seems really nice and feature rich, but ran slow on my ATI Radeon 3100, if I had 2 or 3 thing going at once my videos would lag when I tried dragging a window.  On top of that, although all my KDE apps would render sound simultaneously, if I tried to play a game or something while music was playing, the game would have no sound.  There were just a few minor annoyances, KDE just seems to BIG for me, I feel comfortable working in Gnome, so I'm probably going to stay here.  If anybody else has installed KDE by just marking the "kubuntu-desktop" package in synaptic and you want to remove it, here's the file I saved with the markings that you can read into synaptic and it will remove everything installed by kubuntu-desktop so you won't have to worry about worthless kde packages sitting around after you've nuked the DE.  Just copy and paste this into a text file and save it, then open Synaptic, click "File" and then click "Read Markings".

```

python-packagekit		deinstall
ksystemlog		deinstall
libqscintilla2-5		deinstall
libpackagekit-glib11		deinstall
krdc		deinstall
krfb		deinstall
kde-zeroconf		deinstall
kppp		deinstall
userconfig		deinstall
libkonq5-templates		deinstall
libqca2		deinstall
kipi-plugins		deinstall
libksane0		deinstall
update-notifier-kde		deinstall
libkonqsidebarplugin4		deinstall
kdebase-runtime-data-common		deinstall
libpolkit-dbus2		deinstall
libkorundum4-ruby1.8		deinstall
kubuntu-default-settings		deinstall
libqt4-qt3support		deinstall
kubuntu-desktop		deinstall
kubuntu-firefox-deinstaller		deinstall
libqt4-phonon		deinstall
libkabcommon4		deinstall
ktorrent-data		deinstall
libk3b6		deinstall
kpackagekit		deinstall
plasma-widget-facebook		deinstall
libindicate-qt0		deinstall
libqca2-plugin-ossl		deinstall
ksnapshot		deinstall
libpolkit-qt0		deinstall
libkipi6		deinstall
kdepim-groupware		deinstall
libotr2		deinstall
libqtscript4-network		deinstall
konqueror-nsplugins		deinstall
libqt4-test		deinstall
libqt4-script		deinstall
libknotificationitem1		deinstall
libqt4-designer		deinstall
libkleo4		deinstall
libqt4-network		deinstall
libqt4-dbus		deinstall
language-selector-qt		deinstall
libsmokeqt4-2		deinstall
libqtscript4-gui		deinstall
plasma-widget-kimpanel		deinstall
gwenview		deinstall
kdelibs5		deinstall
kubuntu-docs		deinstall
printer-applet		deinstall
quassel		deinstall
libboost-program-options1.38.0		deinstall
plasma-scriptengine-python		deinstall
libkontactinterfaces4		deinstall
klipper		deinstall
libmimelib4		deinstall
plasma-widget-kubuntu-qa-feedback		deinstall
kaddressbook		deinstall
kontact		deinstall
kdebase-workspace-bin		deinstall
kwalletmanager		deinstall
usb-creator-kde		deinstall
libpoppler-qt4-3		deinstall
ibus-qt4		deinstall
libkexiv2-7		deinstall
ksysguard		deinstall
libokularcore1		deinstall
libtag-extras1		deinstall
libexiv2-5		deinstall
mysql-server-core-5.1		deinstall
libkcddb4		deinstall
konq-plugins		deinstall
apturl-kde		deinstall
libscim8c2a		deinstall
kdepim-kresources		deinstall
libqtscript4-sql		deinstall
kdegraphics-strigi-plugins		deinstall
libqt4-opengl		deinstall
dolphin		deinstall
plasma-dataengines-addons		deinstall
khelpcenter4		deinstall
kdesudo		deinstall
policykit		deinstall
k3b-data		deinstall
libqtscript4-xml		deinstall
kde-style-qtcurve		deinstall
libqt4-xmlpatterns		deinstall
libqt4-sql-sqlite		deinstall
pinentry-gtk2		deinstall
libsmokekde4-2		deinstall
libakonadiprivate1		deinstall
konsole		deinstall
libstrigiqtdbusclient0		deinstall
korganizer		deinstall
openoffice.org-kde		deinstall
k3b		deinstall
libsoprano4		deinstall
ktimetracker		deinstall
akonadi-server		deinstall
akregator		deinstall
openoffice.org-style-oxygen		deinstall
kde-icons-oxygen		deinstall
libqt4-help		deinstall
python-qt4		deinstall
kamera		deinstall
ijsgutenprint		deinstall
ark		deinstall
libkpgp4		deinstall
kde-window-manager		deinstall
libclucene0ldbl		deinstall
konqueror-plugins		deinstall
kvkbd		deinstall
libkonq5		deinstall
libkdepim4		deinstall
amarok-utils		deinstall
plasma-widget-indicatordisplay		deinstall
libkdecorations4		deinstall
libqimageblitz4		deinstall
gtk2-engines-qtcurve		deinstall
python-sip4		deinstall
phonon-backend-xine		deinstall
libksieve4		deinstall
kfind		deinstall
ttf-arphic-uming		deinstall
dragonplayer		deinstall
kdebase-bin		deinstall
kdepimlibs-data		deinstall
plasma-widget-folderview		deinstall
kdm		deinstall
speedcrunch		deinstall
pinentry-qt4		deinstall
amarok		deinstall
gnupg-agent		deinstall
libpolkit-grant2		deinstall
software-properties-kde		deinstall
libpackagekit-qt11		deinstall
libvncserver0		deinstall
libao2		deinstall
amarok-common		deinstall
libkwineffects1		deinstall
plasma-widgets-addons		deinstall
knotes		deinstall
soprano-daemon		deinstall
kdepim-runtime-libs4		deinstall
libqt4-sql		deinstall
foomatic-db-gutenprint		deinstall
libkopete4		deinstall
libqt4-svg		deinstall
kdebase-workspace-data		deinstall
kdebase-workspace-libs4+5		deinstall
konqueror		deinstall
libqt4-xml		deinstall
libzip1		deinstall
deinstall-package		deinstall
cdrdao		deinstall
kdebase-workspace-kgreet-plugins		deinstall
packagekit		deinstall
libqt4-assistant		deinstall
gdebi-kde		deinstall
libplasma3		deinstall
libqt4-ruby1.8		deinstall
plasma-dataengines-workspace		deinstall
plasma-widget-lancelot		deinstall
ksysguardd		deinstall
kdepimlibs5		deinstall
update-manager-kde		deinstall
plasma-widget-quickaccess		deinstall
kdelibs-bin		deinstall
kdebluetooth		deinstall
kwin-style-qtcurve		deinstall
kdepim-runtime-data		deinstall
ktorrent		deinstall
jockey-kde		deinstall
liblancelot0		deinstall
kdemultimedia-kio-plugins		deinstall
libstreams0		deinstall
python-qt4-dbus		deinstall
libqt4-webkit		deinstall
libepub0		deinstall
konq-plugins-l10n		deinstall
exiv2		deinstall
kopete		deinstall
kdelibs5-data		deinstall
plasma-widget-googlecalendar		deinstall
kdebase-runtime		deinstall
quassel-data		deinstall
libqtscript4-uitools		deinstall
kdepim-wizards		deinstall
kdebase-data		deinstall
libqt4-sql-mysql		deinstall
kate		deinstall
kmail		deinstall
liblastfm0		deinstall
libqt4-scripttools		deinstall
kubuntu-artwork-usplash		deinstall
libqtscript4-core		deinstall
systemsettings		deinstall
kdebase-runtime-data		deinstall
kdebase-plasma		deinstall
system-config-printer-kde		deinstall
apport-kde		deinstall
kdepim-runtime		deinstall
kdebase-runtime-bin-kde4		deinstall
oxygen-cursor-theme		deinstall
plasma-widget-networkmanagement		deinstall
konqueror-plugin-searchbar		deinstall
okular		deinstall
kmousetool		deinstall
kdepim-strigi-plugins		deinstall
plasma-widgets-workspace		deinstall
libmsn0.1		deinstall
hpijs-ppds		deinstall
kmag		deinstall
libkdcraw7		deinstall
kubuntu-konqueror-shortcuts		deinstall
python-kde4		deinstall
okular-extra-backends		deinstall
kdepasswd		deinstall
kmix		deinstall
libstreamanalyzer0		deinstall
libpolkit2		deinstall
kcm-gtk		deinstall
packagekit-backend-apt		deinstall

```

Edit:  Just so you know where I got this list of things to remove, all I did was after I hit install on kubuntu-desktop, I saved the markings, then did a find/replace and replaced every occurrence of the word "install" with the word "deinstall".  Just thought I'd let you know that I didn't start picking random packages from memory.

---

### Post by lovinglinux on 2009-11-21
> **marcusdean.adams said:**
> Edit:  Just so you know where I got this list of things to remove, all I did was after I hit install on kubuntu-desktop, I saved the markings, then did a find/replace and replaced every occurrence of the word "install" with the word "deinstall".  Just thought I'd let you know that I didn't start picking random packages from memory.


[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

