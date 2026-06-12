---
title: "Get rid of all gnome stuff (delete that DE)"
date: 2017-06-18
forum: Desktop Environments
---

### Post by josefranw on 2017-06-18
Hello, friends.

I have recently (a few weeks) installed LUBUNTU on my laptop. Everything was O.K. but a few days ago I decided to "give it a go" to Gnome so I installed it using the command found [here]("https://askubuntu.com/questions/306282/can-i-change-my-ubuntu-install-into-a-different-flavour-like-kubuntu"). I then decided to uninstall it after confirming it was too heavy or my old laptop... I have LXDE once again, but I think some remnants of Gnome are installed and, for some reason, I also feel that the laptop is slower than before the installation.

I just want to make sure I have successfully deleted all Gnome components from my laptop and that only lubuntu's stuff are installed. 

I have deleted something that have the gnome- thing in its name but I don't know if it is safe to do so.

How can I check my distribution is "gnome-cleaned"? 

There's also some funny thing happening with the Icons. Some of them have disappeared; as in here:

---

### Post by lisati on 2017-06-18
Do you have another image that illustrates your question?

---

### Post by #&amp;thj^% on 2017-06-18
Give this a try:
```
sudo apt-get autoremove --purge ubuntu-desktop
```
Followed by, just for good measure 
```
sudo apt-get autoremove
```

---

### Post by josefranw on 2017-06-18
[https://ibb.co/dK93yQ](https://ibb.co/dK93yQ)

---

### Post by josefranw on 2017-06-18
Yes, I had already done that. It says the package is not installed so it deletes nothing...

---

### Post by #&amp;thj^% on 2017-06-18
_**EDIT: This also assumes you have already made good back-ups of things you want safe from possible breakage.**_
Well this should remove the bulk of it.
```
sudo apt-get purge unity ubuntu-system-settings
```

And again run:
```
sudo apt autoremove
```

[COLOR=#ff0000][B]Special Note and Please Read carefully:***Warning you are on your own here, I will not be responsible if this breaks your system***


[/B][/COLOR]Ubuntu comes with a lot of GNOME applications pre-installed for giving the users an overall good desktop experience. Many of them have a deep system integration ... so it's not recommended to remove them - a good example is nautilus. But there are features that are quite safe to remove ... 
As this is an aspect being more opinion based ... I give you a list of packages that I have removed before: (Again your mileage may vary)
```
account-plugin-aim  
account-plugin-facebook  
account-plugin-flickr  
account-plugin-jabber  
account-plugin-salut  
account-plugin-yahoo  
aisleriot  
gnome-mahjongg  
gnome-mines  
gnome-sudoku  
landscape-client-ui-install  
unity-lens-music  
unity-lens-photos  
unity-lens-video  
unity-scope-audacious  
unity-scope-chromiumbookmarks  
unity-scope-clementine  
unity-scope-colourlovers  
unity-scope-devhelp  
unity-scope-firefoxbookmarks  
unity-scope-gmusicbrowser  
unity-scope-gourmet  
unity-scope-guayadeque  
unity-scope-musicstores  
unity-scope-musique  
unity-scope-openclipart  
unity-scope-texdoc  
unity-scope-tomboy  
unity-scope-video-remote  
unity-scope-virtualbox  
unity-scope-zotero  
unity-webapps-common
```

To remove compiz:
```
sudo apt-get autoremove --purge compiz compiz-gnome compiz-plugins-default libcompizconfig0
```

If your not using Nautilus:
```
sudo apt-get autoremove --purge nautilus nautilus-sendto nautilus-sendto-empathy nautilus-share

```
Zeitgeist, which is considered intrusive by many users, this will also free some memory and reduce hard disk access.

```
zeitgeist-daemon --quit
sudo apt-get autoremove --purge activity-log-manager-common python-zeitgeist rhythmbox-plugin-zeitgeist zeitgeist zeitgeist-core zeitgeist-datahub
```

So you see, you will have to** at your own risk here,** remove extras that gets pulled in.
Good Luck. :D

---

### Post by vasa1 on 2017-06-19
> **josefranw said:**
> Yes, I had already done that. It says the package is not installed so it deletes nothing...Well, you didn't tell 1fallen the exact command you followed from the link you provided in your first post!

So, from all of```
Ubuntu:
sudo apt-get install ubuntu-desktop
Kubuntu:
sudo apt-get install kubuntu-desktop
Xubuntu:
sudo apt-get install xubuntu-desktop
Lubuntu:
sudo apt-get install lubuntu-desktop
Ubuntu GNOME:
sudo apt-get install ubuntu-gnome-desktop
```
was it the first or the last one?

And, re.> There's also some funny thing happening with the Icons. Some of them have disappeared; as in here:show us some more pics with different applications.

---

### Post by josefranw on 2017-06-23
> **vasa1 said:**
> Well, you didn't tell 1fallen the exact command you followed from the link you provided in your first post!

So, from all of```
Ubuntu:
sudo apt-get install ubuntu-desktop
Kubuntu:
sudo apt-get install kubuntu-desktop
Xubuntu:
sudo apt-get install xubuntu-desktop
Lubuntu:
sudo apt-get install lubuntu-desktop
Ubuntu GNOME:
sudo apt-get install ubuntu-gnome-desktop
```
was it the first or the last one?

It was the last one.

> **vasa1 said:**
> And, re.show us some more pics with different applications.

Yes, not only have some icons disappeared but also some applications' menus display incorrectly, like with no boarders or separation from each item. I suppose you call this "composing"?:confused:

[ATTACH=CONFIG]275754[/ATTACH][ATTACH=CONFIG]275755[/ATTACH][ATTACH=CONFIG]275753[/ATTACH]

---

### Post by #&amp;thj^% on 2017-06-23
> **josefranw said:**
> It was the last one.



Yes, not only have some icons disappeared but also some applications' menus display incorrectly, like with no boarders or separation from each item. I suppose you call this "composing"?:confused:

[ATTACH=CONFIG]275754[/ATTACH][ATTACH=CONFIG]275755[/ATTACH][ATTACH=CONFIG]275753[/ATTACH]

That would have been good to know at the begining.
That's as much my fault as anyone's for not asking though.
The bad thing about installing other Desktop environments is they install a lot of extra packages and it is sometimes hard to find and remove all of them. 
This should remove the Lions Share of them:
```
sudo apt-get purge abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview alacarte argyll cups-pk-helper epiphany-browser epiphany-browser-data evolution evolution-common evolution-plugins fonts-cantarell fonts-lyx gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-gst-2.0 gir1.2-evince-3.0 gir1.2-gck-1 gir1.2-gconf-2.0 gir1.2-gcr-3 gir1.2-gdesktopenums-3.0 gir1.2-gkbd-3.0 gir1.2-gnomedesktop-3.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-ibus-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-panelapplet-4.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs glchess glines gnect gnibbles gnobots2 gnome-applets gnome-applets-data gnome-color-manager gnome-desktop-data gnome-dictionary gnome-games gnome-games-extra-data gnome-icon-theme-extras gnome-mahjongg gnome-packagekit gnome-packagekit-data gnome-panel gnome-panel-data gnome-search-tool gnome-session-fallback gnome-shell gnome-shell-common gnome-software-manager gnome-sushi gnome-tweak-tool gnome-update-viewer gnotravex gnotski gnumeric gnumeric-common gnumeric-doc gstreamer1.0-alsa gstreamer1.0-plugins-base-apps gstreamer1.0-pulseaudio gstreamer1.0-tools gtali iagno itstool libabiword-2.9 libaudit0 libcaribou-common libcaribou0 libcolamd2.7.1 libcolord-gtk1 libedataserverui-3.0-4 libevolution libgdict-1.0-6 libgdict-common libgdome2-0 libgdome2-cpp-smart0c2a libgjs0c libgoffice-0.8-8 libgoffice-0.8-8-common libgtkmathview0c2a libicc2 libimdi0 libiptcdata0 liblink-grammar4 libloudmouth1-0 libmail-spf-perl libmozjs185-1.0 libmutter0 libnetaddr-ip-perl libots0 libpst4 libtidy-0.99-0 libtracker-extract-0.14-0 libtracker-miner-0.14-0 libtracker-sparql-0.14-0 libwv-1.2-4 libytnef0 lightsoff link-grammar-dictionaries-en mutter mutter-common packagekit packagekit-backend-aptcc packagekit-tools plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text python-cloudfiles python-packagekit quadrapassel re2c simple-scan spamassassin spamc swell-foop tracker tracker-extract tracker-gui tracker-miner-fs tracker-utils ubuntu-gnome-default-settings ubuntu-gnome-desktop xsltproc yelp-tools

```

Then run:
```
sudo apt-get autoremove
```
If you chose GDM you will have to run this also before rebooting.
```

sudo dpkg-reconfigure gdm
```
Hit enter at the prompt and then select <lightdm> from the options. After that you can purge gdm with
```

sudo apt-get purge gdm  
```
Now for good messure run this:
```
sudo apt-get --reinstall install lubuntu-desktop
```
**_Again I assume you have made backups of the important files you want to keep safe form a broken system._**

---

### Post by josefranw on 2017-06-23
Thank you for answering. I have done what you have suggested and no package was removed because they all say they were not installed so, I must assume all gnome components (I don't know what to call this) had already been removed. 

Unfortunately the thing about some applications menus is still happening. What can this be?

Should I open a new thread for that topic or not?

---

### Post by #&amp;thj^% on 2017-06-23
> **josefranw said:**
> Thank you for answering. I have done what you have suggested and no package was removed because they all say they were not installed so, I must assume all gnome components (I don't know what to call this) had already been removed. 

Unfortunately the thing about some applications menus is still happening. What can this be?

Should I open a new thread for that topic or not?

Should be ok here no need to open another.
But did you run this one:
```
sudo apt-get --reinstall install lubuntu-desktop
```
But I'm having a tough time with nothing being removed with that long string I gave you.
By the sounds of it... you are not giving me some important information needed here to help.
What steps have you done since you first installed the gnome-desktop, Very important to know here so that I don't mislead you or blow-up your system.
And from your latest pictures this looks more like a bad theme being used... Try a different theme to see if there is any improvement.
Got to go for the evening...I'll check back with you later/tomorrow. 
Cheers

---

### Post by josefranw on 2017-06-23
> **1fallen said:**
> Should be ok here no need to open another.
But did you run this one:
```
sudo apt-get --reinstall install lubuntu-desktop
```
But I'm having a tough time with nothing being removed with that long string I gave you.
By the sounds of it... you are not giving me some important information needed here to help.
What steps have you done since you first installed the gnome-desktop, Very important to know here so that I don't mislead you or blow-up your system.
Cheers

Yes, I did. I ran all of them. It had already followed other tutorials to delete the desktop enviorement, so I guessed that's why everything was already deleted.

I used
sudo apt-get remove ubuntu-gnome-desktop
sudo apt-get remove gnome-shell 
I also manually searched for things that contained gnome in their name via synaptic and deleted some of them (when I didn't get any message that other packages would be deleted also... but I can't remember what I deleted). That's why I wanted to know if there was a way to check if my system was "gnome-free" if you know what I mean. By the looks of it, it apparently is.


> **1fallen said:**
> 
And from your latest pictures this looks more like a bad theme being used... Try a different theme to see if there is any improvement.
Got to go for the evening...I'll check back with you later/tomorrow. 
Cheers
 
Yes, I have checked and all other options (except lubuntu default) have problems with displaying correctly. For some, menus show properly but some icons are still missing. Only "Lubuntu" default icons and controls show properly.

Thanks for your valuable help.

---

### Post by vasa1 on 2017-06-23
> **1fallen said:**
> ...
But I'm having a tough time with nothing being removed with that long string I gave you.
...
That list had abiword and gnumeric, both of which are part of Lubuntu.

Recalling> I just want to make sure I have successfully deleted all Gnome components from my laptop and that only lubuntu's stuff are installed. it appears that you've lost some Lubuntu software also.

---

### Post by josefranw on 2017-06-23
Well, this is what I get:

```
josefranw@josefranw-3000-N200:~$ sudo apt-get purge abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview alacarte argyll cups-pk-helper epiphany-browser epiphany-browser-data evolution evolution-common evolution-plugins fonts-cantarell fonts-lyx gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-gst-2.0 gir1.2-evince-3.0 gir1.2-gck-1 gir1.2-gconf-2.0 gir1.2-gcr-3 gir1.2-gdesktopenums-3.0 gir1.2-gkbd-3.0 gir1.2-gnomedesktop-3.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-ibus-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-panelapplet-4.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs glchess glines gnect gnibbles gnobots2 gnome-applets gnome-applets-data gnome-color-manager gnome-desktop-data gnome-dictionary gnome-games gnome-games-extra-data gnome-icon-theme-extras gnome-mahjongg gnome-packagekit gnome-packagekit-data gnome-panel gnome-panel-data gnome-search-tool gnome-session-fallback gnome-shell gnome-shell-common gnome-software-manager gnome-sushi gnome-tweak-tool gnome-update-viewer gnotravex gnotski gnumeric gnumeric-common gnumeric-doc gstreamer1.0-alsa gstreamer1.0-plugins-base-apps gstreamer1.0-pulseaudio gstreamer1.0-tools gtali iagno itstool libabiword-2.9 libaudit0 libcaribou-common libcaribou0 libcolamd2.7.1 libcolord-gtk1 libedataserverui-3.0-4 libevolution libgdict-1.0-6 libgdict-common libgdome2-0 libgdome2-cpp-smart0c2a libgjs0c libgoffice-0.8-8 libgoffice-0.8-8-common libgtkmathview0c2a libicc2 libimdi0 libiptcdata0 liblink-grammar4 libloudmouth1-0 libmail-spf-perl libmozjs185-1.0 libmutter0 libnetaddr-ip-perl libots0 libpst4 libtidy-0.99-0 libtracker-extract-0.14-0 libtracker-miner-0.14-0 libtracker-sparql-0.14-0 libwv-1.2-4 libytnef0 lightsoff link-grammar-dictionaries-en mutter mutter-common packagekit packagekit-backend-aptcc packagekit-tools plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text python-cloudfiles python-packagekit quadrapassel re2c simple-scan spamassassin spamc swell-foop tracker tracker-extract tracker-gui tracker-miner-fs tracker-utils ubuntu-gnome-default-settings ubuntu-gnome-desktop xsltproc yelp-tools[sudo] password for josefranw: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete «gdm» no está instalado, no se eliminará
El paquete «glchess» no está instalado, no se eliminará
El paquete «glines» no está instalado, no se eliminará
El paquete «gnect» no está instalado, no se eliminará
El paquete «gnibbles» no está instalado, no se eliminará
El paquete «gnobots2» no está instalado, no se eliminará
El paquete «gnome-session-fallback» no está instalado, no se eliminará
El paquete «gnome-software-manager» no está instalado, no se eliminará
El paquete «gnotravex» no está instalado, no se eliminará
El paquete «gnotski» no está instalado, no se eliminará
El paquete «gtali» no está instalado, no se eliminará
El paquete «libaudit0» no está instalado, no se eliminará
El paquete «libgdome2-cpp-smart0c2a» no está instalado, no se eliminará
El paquete «libgjs0c» no está instalado, no se eliminará
El paquete «libmutter0» no está instalado, no se eliminará
El paquete «libtidy-0.99-0» no está instalado, no se eliminará
El paquete «packagekit-backend-aptcc» no está instalado, no se eliminará
El paquete «python-packagekit» no está instalado, no se eliminará
El paquete «tracker-utils» no está instalado, no se eliminará
E: No se ha podido localizar el paquete abiword-plugin-mathview
E: No se ha podido localizar el paquete gir1.2-clutter-gst-2.0
E: No se pudo encontrar ningún paquete usando «*» con «gir1.2-clutter-gst-2.0»
E: No se pudo encontrar ningún paquete con la expresión regular «gir1.2-clutter-gst-2.0»
E: No se ha podido localizar el paquete gir1.2-mutter-3.0
E: No se pudo encontrar ningún paquete usando «*» con «gir1.2-mutter-3.0»
E: No se pudo encontrar ningún paquete con la expresión regular «gir1.2-mutter-3.0»
E: No se ha podido localizar el paquete gir1.2-panelapplet-4.0
E: No se pudo encontrar ningún paquete usando «*» con «gir1.2-panelapplet-4.0»
E: No se pudo encontrar ningún paquete con la expresión regular «gir1.2-panelapplet-4.0»
E: No se ha podido localizar el paquete gnome-desktop-data
E: No se ha podido localizar el paquete gnome-games-extra-data
E: No se ha podido localizar el paquete gnome-update-viewer
E: No se ha podido localizar el paquete libabiword-2.9
E: No se pudo encontrar ningún paquete usando «*» con «libabiword-2.9»
E: No se pudo encontrar ningún paquete con la expresión regular «libabiword-2.9»
E: No se ha podido localizar el paquete libcolamd2.7.1
E: No se pudo encontrar ningún paquete usando «*» con «libcolamd2.7.1»
E: No se pudo encontrar ningún paquete con la expresión regular «libcolamd2.7.1»
E: No se ha podido localizar el paquete libedataserverui-3.0-4
E: No se pudo encontrar ningún paquete usando «*» con «libedataserverui-3.0-4»
E: No se pudo encontrar ningún paquete con la expresión regular «libedataserverui-3.0-4»
E: No se ha podido localizar el paquete libgdict-1.0-6
E: No se pudo encontrar ningún paquete usando «*» con «libgdict-1.0-6»
E: No se pudo encontrar ningún paquete con la expresión regular «libgdict-1.0-6»
E: No se ha podido localizar el paquete libicc2
E: No se ha podido localizar el paquete libimdi0
E: No se ha podido localizar el paquete liblink-grammar4
E: No se ha podido localizar el paquete libtracker-extract-0.14-0
E: No se pudo encontrar ningún paquete usando «*» con «libtracker-extract-0.14-0»
E: No se pudo encontrar ningún paquete con la expresión regular «libtracker-extract-0.14-0»
E: No se ha podido localizar el paquete libtracker-miner-0.14-0
E: No se pudo encontrar ningún paquete usando «*» con «libtracker-miner-0.14-0»
E: No se pudo encontrar ningún paquete con la expresión regular «libtracker-miner-0.14-0»
E: No se ha podido localizar el paquete libtracker-sparql-0.14-0
E: No se pudo encontrar ningún paquete usando «*» con «libtracker-sparql-0.14-0»
E: No se pudo encontrar ningún paquete con la expresión regular «libtracker-sparql-0.14-0»
josefranw@josefranw-3000-N200:~$ 
```

---

### Post by #&amp;thj^% on 2017-06-24
> **vasa1 said:**
> **_That list had abiword and gnumeric, both of which are part of Lubuntu._**

Recallingit appears that you've lost some Lubuntu software also.

Thanks for pointing that out vasa1, but it would appear those were already removed prior to this.
And I have never installed Lubuntu...But good to know.
@ josefranw here is a list of the software installed with Lubuntu only no gnome-desktop.
You may need to go through the list with synaptic if that is easier for you, and go down the list to be sure everything is installed.
[https://paste.ubuntu.com/24941422/](https://paste.ubuntu.com/24941422/)
Now after everything is back to a Lubuntu Desktop...reboot and fingers crossed all should be the way it was when first installed.
Good Luck:)

---

### Post by josefranw on 2017-06-24
> **1fallen said:**
> @ josefranw here is a list of the software installed with Lubuntu only no gnome-desktop.
You may need to go through the list with synaptic if that is easier for you, and go down the list to be sure everything is installed.
[https://paste.ubuntu.com/24941422/](https://paste.ubuntu.com/24941422/)
Now after everything is back to a Lubuntu Desktop...reboot and fingers crossed all should be the way it was when first installed.
Good Luck:)

All right. Thank you...

---

