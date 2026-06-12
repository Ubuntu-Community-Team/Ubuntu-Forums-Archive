---
title: "Kubuntu the K-way"
date: 2005-05-13
forum: Desktop Environments
---

### Post by Terracotta on 2005-05-13
Hye,

since to me the kubuntu installation is too bloated
I tried today to install kubuntu like this:

server install

after installation I went on like this:

sudo aptitude install kde-core
sudo aptitude install kdm
and then I went on with the nvidia drivers
(sudo apt-get install nvidia-glx
 sudo apt-get install nvidia-settings
 cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
 sudo nvidia-glx-config enable)

When I came to the  cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup part kubuntu sais there is no such file, so I take it xorg isn't installed,
Can anyone help me to set up a kde only kubuntu system, with no apps like firefox or openoffice installed? Since I apparently can't uninstall openoffice.org or firefox or ...
I have an amd 64 3500+ and I use kubuntu 5.04 x86_64.

Ps, I always HAVE to use the server install since there is a problem with xorg, nvidia and 64 bit :-s, but normally I used "aptitude kubuntu-desktop" wich installed way too much if you ask me  :mad: ).

---

### Post by Jens Bache-Wiig on 2005-05-13
Thanks for the tip. I have been looking for a way to install KDE without completely filling my menus with useless stuff. I think the kubuntu-desktop package could be trimmed down a  lot. There is no need to include every possible kde app available.

---

### Post by Terracotta on 2005-05-13
Euhm, it's not a tip, I posted because it didn't work, although according to the kubuntu wiki it should work.
If you're going to  install the kubuntu-desktop you're gonna get your menu's filled :-), I think :s

Anyway if it helped, I'm glad I could help someone  \\:D/

---

### Post by tardis_junkie on 2005-05-13
I do much the same - install as server then I install kubuntu-desktop, this also gets round the update problem with kdelibs.

To do it the way you are dooing it you are going to have to install all the base x components as well.

eg.

sudo apt-get install xserver-xorg

but you will still have to probably edit all the startup files yourself and the kubuntu custimisation will also be missing (you might prefer that).

Have you tried apt-get removing open office etc to clean your system.

Hope this helps.

---

### Post by philipacamaniac on 2005-05-13
You mentioned Firefox inclusion, but it isn't a part of the kubuntu-desktop package. Firefox is only a part of the ubuntu-desktop package. The only non-kde app that is included with Kubuntu is OpenOffice. BTW, have you ever seen a default KDE installation, such as on vanilla Debian, Slackware or elsewhere? It has a TON of bloatware, with menus upon menus galore. Kubuntu is actually rather an awesome refresher from the usual KDE bloat.

Kubuntu has only what almost everyone needs on a desktop: office suite, music player, video player, image viewer, personal information manager, web browser, instant messenger, system admin tools and various necessary utilities. If you aren't using all that, why even use KDE? I love the XFCE window manager, and I would totally use it if I didn't have a need for a fully capable desktop environment.

Oh, and off the record, there are about a bazillion good and bad KDE apps over at kde-apps.org, of which most are NOT included. Even the official KOffice Suite is not included.

Anyway, to be of some helpfulness, apt-get installing xorg will help, and it will come up with a configure screen once it installs.

---

### Post by Terracotta on 2005-05-14
Firefox IS included in the kubuntu-desktop package (I think they listened to their users :-), wich actually is a good thing), but I prefer one thing that does the trick and konqueror seems to be more than capable to replace firefox. I tried to uninstall openoffice, but as mentioned I didn't succeed, don't ask me why, I opened kynaptic, searched for openoffice and firefox and selected to remove it. it gave a warning kubuntu-desktop would have to be deleted as well, I said ok but nothing happened, openoffice was still there.

@philipacamaniac: you're right, other kde distro's are much more bloated :-), but what I ment is this: isn't it possible to make some kind of script that detects what hardware is included and that makes desitions based on the result to install some software, for example, kwifimanager is installed, I don't need it at all, since I don't have a wifi-card but it still shows up in my menu's, if I want to uninstall it I have to uninstall the kubuntu-desktop package as well. Same goes for music: why two music players (well three actually if you count Kscd as one)? Ps: thank god not all kde-apps are included. I think indeed the kubuntu-people succeeded in making a not too bloated configuration, but there still are a lot of apps I don't use :-), maybe I might in the future but not at this time.

@ tardis-juniki: I think the editing and customisation can be accomplished by installing:

sudo aptitude install kubuntu-default-settings


PS: I was just telling how I'ld like to have my own desktop organised, I didn't succeed in creating it on my own, the reason I use a desktop environment is because everything is accustomed to each and every app, (for example kparts is quite nice :-) ), I love the way it looks and the reason I use Koffice over openoffice is because I would love to see that one grow: it's faster, and it's better integrated in the system, and it still fullfills my needs, if it's installed, one doesn't have to :-). I think the apt-get install xserver-xorg has helped me the most :-), I tried apt-get install xorg wich euhm  :-# didn't work, my mistake :-).

---

### Post by seijuro on 2006-12-08
why not just edit your menu and remove it if that is really what is bothering you so badly. Right click the K menu click menu editor delete the entries you don't want to show and save.

---

