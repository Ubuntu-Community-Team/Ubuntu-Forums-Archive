---
title: "Font problem after updates"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Shimmy on 2006-08-17
Hi, i'm having some problems with the fonts since last update. I think it was after last update, i've also played a bit with gcompizthemer since i run compiz.. but i don't think it's a compiz issue, i have the same problem when i don't run compiz..

The problem is that the fonts are bigger than they use to be, the bold fonts looks really ugly.. 

The font in active Tab in firefox are very bold and also the font for new emails in firefox. The rest of the fonts looks ok, it's just this bold one that looks too bold.. have a look at the screenshot

---

### Post by huwshimi on 2006-08-17
Bump this. Antialiasing etc. gone funny. Something to do with Cairo update?

---

### Post by Helldesigner on 2006-08-17
Exactly the same here... It's the last libfreetype and cairo2 update - I know  because I've got the habit of restarting after each update to see if nothing has gone south (bad experience with compiz decorations in the past). 

In my case the hinting was messed up too (I've got LCD, so subpixel hinting was my choice). I had to scout the forum to look for some clues - like inserting the .fonts.conf file into my ~ folder - the file looks like this:

[HTML]<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign"><bool>true</bool></edit>
  </match>
</fontconfig>[/HTML]

It has fixed my ugly hinting, but the extremly-ugly-bold issue remains. Plus, some fonts in Thunderbird are more than hideous - bolder than they should, with broken hinting - some letters are "eating" others etc.

Oh, and just for the record - I did the:

```
dpkg-recofigure fontconfig
```

and experimented with different settings. No luck. Of course - the standard gnome font config utility (System -> prefs -> fonts) doesn't do any good either.

Any ideas? Anyone?

---

### Post by Shimmy on 2006-08-17
Helldesigner, Thanks for your response, i'm gonna try your suggestions and see if things gets better.. too bad the bold-font problem still exists, thats what irritates me most. Hopfully someone find a solution to this.

---

### Post by Helldesigner on 2006-08-17
No problem. Unfortunatelly, it's not even close to what we've (or at least I have) had before this unfortunate update :/ I hope someone will post some fix soon, too...

---

### Post by givré on 2006-08-17
It seams to be an upgrade from compiz repo (apparently to add true transparency in gnome-terminal, but that don't work for me)
I try to reverse to the previous version but it's quite a pain between all those package.
I think the way to do is:
- disable compiz repo
- update
- revert to previous version (have a look at history) with force version
- block the package you just change
- reenable compiz repo

---

### Post by Helldesigner on 2006-08-17
Hm, and is there any way to tell where does a package come from? Cause both libfreetype and cairo2 have "ubuntu" in their version names in my case:

- libfreetype 2.2.1.-0ubuntu1
- libcairo2 1.2.2.-0ubuntu1

And what's especially annoying - if I try to revert libfreetype to the previous version (although i wouldn't like to do it, 'cause if it's a new version, it's SUPPOSED to work better than the older one, right?) -- Synaptic is telling  me I need to uninstall virtually every X app I've got.

---

### Post by givré on 2006-08-17
```
apt-cache showpkg libfreetype6
```
and check the Versions category (on top).
revert to the previous version is quite a pain,
- you need to first reinstall the last version of gnome-terminal
- after python-vte
- after libvte
- and to finish libfreetype6.
and the last didn't really work for me, i add to install it with a version i had via dpkg, so i hope compiz guys will provide a fix for that soon, it's already discuss there : [http://www.compiz.net/topic-3116-fonts-are-now-complete-crap](http://www.compiz.net/topic-3116-fonts-are-now-complete-crap)

---

### Post by Helldesigner on 2006-08-17
> **givré said:**
> ```
apt-cache showpkg libfreetype6
```
and check the Versions category (on top).
revert to the previous version is quite a pain,
- you need to first reinstall the last version of gnome-terminal
- after python-vte
- after libvte
- and to finish libfreetype6.
and the last didn't really work for me, i add to install it with a version i had via dpkg, so i hope compiz guys will provide a fix for that soon, it's already discuss there : [http://www.compiz.net/topic-3116-fonts-are-now-complete-crap](http://www.compiz.net/topic-3116-fonts-are-now-complete-crap)

Thanks for the hint with dpkg. And yeah, when I tried to revert back to older cairo2 and libfreetype, I ended up in CLI reinstalling my entire ubuntu-desktop. This sucks :/ I hope they will fix that ASAP too.

---

### Post by Shimmy on 2006-08-17
Do you think i can just wait until the next update or any update in the future that fixes this font-issue, or do i need to fix it myself?

---

### Post by peabody on 2006-08-17
[http://www.compiz.net/viewtopic.php?pid=25631](http://www.compiz.net/viewtopic.php?pid=25631)

Same topic at the compiz forums.

---

### Post by Helldesigner on 2006-08-17
I will wait for what compiz guys will come up with. Although it's quite a challenge to look at these fonts and not to puke right now :( Damn, and I was so happy to have better looking fonts than I had on windows...

---

### Post by web250 on 2006-08-17
I tried disabling the compiz repos, but then doing a force version (via synaptic) it wants to remove basically everything along with it.

---

### Post by guice on 2006-08-17
I don't see how this is a Compiz issue. It's fonts within applications that got screwed up. I really think it's the libfreetype and cairo2 update that came through not to long ago (this morning?).

I just know I noticed it for the first time not 30 minutes ago when I used my browser for the first time since the latest update.

PS: Here's a screenshot of just how bad the fonts are: [http://www.gpcentre.net/images/swiftfox.png](http://www.gpcentre.net/images/swiftfox.png)

---

### Post by The Oatman on 2006-08-17
Just chiming in with the same problem after today's update. I am also a compiz user. I have some of the same symptoms although they are not as ugly as that last screenshot. Some of my fonts look squished vertically though.

Edit: I messed around with my font settings briefly and when I turned off smoothing they looked as bad as the above screenshot... So you might want to try enabling smoothing until a solution is found...

Edit #2: I downgraded with:
$ sudo aptitude install libfreetype6/dapper-security
and my eyes are thanking me for it!

Edit #3: Ok, so if you do #2 without also doing
sudo aptitude install gnome-terminal=2.14.1-0ubuntu1
you will not be able to start gnome terminal after rebooting...

---

### Post by Uncle Spellbinder on 2006-08-18
I've got things working perfectly with the following settings:

Font - *Swis721 Cn BT* (My font of choice)
Resolution - 96
Font Rendering - *Best Shapes*
Smoothing - *Grayscale*
Hinting - *Medium*
Subpixel Order - *RGB*

---

### Post by givré on 2006-08-18
> **guice said:**
> I don't see how this is a Compiz issue. It's fonts within applications that got screwed up. I really think it's the libfreetype and cairo2 update that came through not to long ago (this morning?).

I just know I noticed it for the first time not 30 minutes ago when I used my browser for the first time since the latest update.

PS: Here's a screenshot of just how bad the fonts are: [http://www.gpcentre.net/images/swiftfox.png](http://www.gpcentre.net/images/swiftfox.png)
This is a compiz repo issue because those update came from the compiz repo, there were not official ubuntu update.

---

### Post by nverhaar on 2006-08-18
I downgraded following The Oatman's instructions, and now my fonts are back to normal as well, PHEW!!

---

### Post by WishMaster on 2006-08-18
_Left side:_ aMSN with tcl/tk8.5 IT USED TO HAVE SMOOTH FONTS
Now it is totally f*ckep up ](*,)
I have 'boxes' instead of spaces *freaking out*

_right side:_ gaim. Look at the blurry bold font ! ](*,)


[IMG]http://img91.imageshack.us/img91/271/fontfuckuv6.jpg[/IMG]



They better fix this soon...

---

### Post by OffHand on 2006-08-18
> **The Oatman said:**
> 
Edit #2: I downgraded with:
$ sudo aptitude install libfreetype6/dapper-security
and my eyes are thanking me for it!

That doesn't seem like a good idea:

sudo apt-get install libfreetype6/dapper-security
Password:
Reading package lists... Done
Building dependency tree... Done
Selected version 2.1.10-1ubuntu2.2 (Ubuntu:6.06/dapper-security) for libfreetype6
The following packages will be REMOVED:
  alacarte at-spi beagle beep-media-player beep-media-player-dev
  bittornado-gui bluez-cups bluez-pin brltty-x11 bug-buddy bum camorama
  cedega-small cgwd cgwd-themes compiz compiz-gnome contact-lookup-applet
  cupsys cupsys-driver-gutenprint dbus-1-utils deskbar-applet eog evince
  file-roller firefox firefox-gnome-support firestarter fontconfig gaim
  gcalctool gconf-editor gdebi gdm gedit gimp gimp-print gimp-python gkrellm
  gkrellm-reminder gkrellmapcupsd gkrellmss gksu gnome-about
  gnome-accessibility-themes gnome-app-install gnome-applets gnome-btdownload
  gnome-control-center gnome-cups-manager gnome-games gnome-icon-theme
  gnome-keyring gnome-mag gnome-media gnome-netstatus-applet gnome-nettool
  gnome-panel gnome-pilot gnome-pilot-conduits gnome-power-manager
  gnome-session gnome-spell gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-themes gnome-utils gnome-volume-manager gnomebaker
  gnopernicus gok gparted gset-compiz gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-good gstreamer0.10-x gthumb gtk2-engines-clearlooks
  gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice
  gtk2-engines-ubuntulooks gtkhtml3.8 gtkorphan gtkpod gucharmap
  hal-device-manager hplip hwdb-client j2re1.4-mozilla-plugin k3b kamera
  kcontrol kdebase-bin kdebase-kio-plugins kdelibs-bin kdelibs4c2a
  kdemultimedia-kio-plugins kdesktop kicker language-selector leafpad
  libarts1c2a libatspi1.0-0 libavahi-qt3-1 libbonoboui2-0 libcairo-java
  libcairo2 libcairo2-dev libdbus-qt-1-1c2 libedataserverui1.2-6 libeel2-2
  libexchange-storage1.2-1 libexo-0.3-0 libfontconfig1 libfontconfig1-dev
  libfreetype6-dev libgail-common libgail-gnome-module libgail17 libgcj7-awt
  libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksuui1.0-1
  libglade2-0 libglade2-dev libglade2.0-cil libglademm-2.4-1c2a
  libglademm-2.4-dev libgnome-desktop-2 libgnome-keyring0
  libgnome2-canvas-perl libgnome2-perl libgnome2.0-cil libgnomecanvas2-0
  libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeui-0
  libgpod0 libgtk-java libgtk-jni libgtk2-gladexml-perl libgtk2-perl
  libgtk2-trayicon-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil
  libgtk2.0-common libgtk2.0-dev libgtkhtml2-0 libgtkhtml3.8-15
  libgtkmm-2.4-1c2a libgtkmm-2.4-dev libgtksourceview1.0-0 libgtkspell0
  libgucharmap4 libgutenprintui2-1 libk3b2 libkcddb1 libkonq4
  liblaunchpad-integration0 liblpint-bonobo0 libmetacity0 libnautilus-burn3
  libnautilus-extension1 libnotify1 libpanel-applet2-0 libpango1.0-0
  libpango1.0-common libpango1.0-dev libpoppler1 libpoppler1-glib libqt3-mt
  librsvg2-2 librsvg2-common libsexy2 libswfdec0.3 libtotem-plparser1 libvte4
  libwnck18 libwxgtk2.6-0 libxfcegui4-4 libxft-dev libxft2 metacity
  mozilla-mplayer mozilla-thunderbird mplayer nautilus nautilus-cd-burner
  nautilus-sendto nicotine notification-daemon nvidia-glx openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-math openoffice.org-writer opera
  poppler-utils python-glade2 python-gnome2 python-gnome2-desktop
  python-gnome2-desktop-dev python-gnome2-dev python-gnome2-extras
  python-gst0.10 python-gtk2 python-gtk2-dev python-launchpad-integration
  python-uno python-vte python-wxgtk2.6 python2.4-cairo python2.4-glade2
  python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras
  python2.4-gtk2 rhythmbox scim scim-gtk2-immodule serpentine sound-juicer
  ssh-askpass-gnome synaptic tangerine-icon-theme tango-icon-theme-common
  totem totem-gstreamer tsclient ubuntu-artwork update-manager update-notifier
  vino vlc vlc-plugin-alsa wxvlc x-window-system-core xbase-clients xchat
  xchat-common xclock xfce4-mcs-manager xfce4-mcs-plugins xfce4-terminal xfd
  xfwm4 xfwm4-themes xlogo xsane xscreensaver xscreensaver-data
  xscreensaver-gl xterm yelp zenity
The following packages will be DOWNGRADED:
  libfreetype6
0 upgraded, 0 newly installed, 1 downgraded, 276 to remove and 0 not upgraded.
Need to get 415kB of archives.
After unpacking 838MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

---

### Post by Aeon17x on 2006-08-18
subsonic_shadow: that's because you used apt-get. This time you use aptitude. ;)

---

### Post by OffHand on 2006-08-19
> **Aeon17x said:**
> subsonic_shadow: that's because you used apt-get. This time you use aptitude. ;)

Hey, that worked  :) I will wait till the next updates now.

---

### Post by brodock on 2006-08-19
> **givré said:**
> It seams to be an upgrade from compiz repo (apparently to add true transparency in gnome-terminal, but that don't work for me)
I try to reverse to the previous version but it's quite a pain between all those package.
I think the way to do is:
- disable compiz repo
- update
- revert to previous version (have a look at history) with force version
- block the package you just change
- reenable compiz repo

i modified my configurations with new "font configs" and it looked less uggly...
i also liked this "antialiasing for all the things".

and that's true about terminal... i haven't noticed... i liked the new one :D

---

### Post by petersjm on 2006-08-19
> **The Oatman said:**
> Just chiming in with the same problem after today's update. I am also a compiz user. I have some of the same symptoms although they are not as ugly as that last screenshot. Some of my fonts look squished vertically though.

Edit: I messed around with my font settings briefly and when I turned off smoothing they looked as bad as the above screenshot... So you might want to try enabling smoothing until a solution is found...

Edit #2: I downgraded with:
$ sudo aptitude install libfreetype6/dapper-security
and my eyes are thanking me for it!

Edit #3: Ok, so if you do #2 without also doing
sudo aptitude install gnome-terminal=2.14.1-0ubuntu1
you will not be able to start gnome terminal after rebooting...

Perfect! This worked for me, Oatman. Many thanks.

---

### Post by Aeon17x on 2006-08-19
> **brodock said:**
> i modified my configurations with new "font configs" and it looked less uggly...
i also liked this "antialiasing for all the things".

and that's true about terminal... i haven't noticed... i liked the new one :D

Can you please tell us what modifications you applied? Screenshots would be great too.

---

### Post by petersjm on 2006-08-19
> **petersjm said:**
> Perfect! This worked for me, Oatman. Many thanks.

Oh, but, btw, I now have all these updates sitting in my systray after downgrading. Should I just ignore them for now? Until the updates get updated?

---

### Post by OffHand on 2006-08-19
> **petersjm said:**
> Oh, but, btw, I now have all these updates sitting in my systray after downgrading. Should I just ignore them for now? Until the updates get updated?

```
sudo gedit /etc/apt/sources.list
```

Put a # before the 2 compiz related repos lines and save.

```
sudo apt-get update
```

---

### Post by WishMaster on 2006-08-19
Let me get this straight...

Things should be back to normal if you do these steps:

> _STEP 1:_ downgrade with:
[COLOR=RoyalBlue]sudo aptitude install libfreetype6/dapper-security[/COLOR]

_STEP 2_:
[COLOR=RoyalBlue] sudo aptitude install gnome-terminal=2.14.1-0ubuntu1[/COLOR]
(so terminal still works after reboot)

_STEP 3_: disable compiz in sources.list
[COLOR=RoyalBlue]sudo gedit /etc/apt/sources.list
[/COLOR] Put a # before the 2 compiz related repos lines and save (so those updates don't show up)

_STEP 4:_ update
[COLOR=RoyalBlue]sudo apt-get update[/COLOR]

edit: okay, that worked for me :)
Although aMSN still displays 'blocks' instead of spaces...

---

### Post by OffHand on 2006-08-19
> **WishMaster said:**
> Let me get this straight...

Things should be back to normal if you do these steps:

Yes. And do a ```
sudo apt-get update
```

---

### Post by petersjm on 2006-08-19
I've commented out compiz in my sources.list file (but I only had one entry, not two). That got rid of most of the updates, but it's still telling me there are two gnome-terminal updates...?

---

### Post by WishMaster on 2006-08-19
Same here... Didn't have the guts to install the terminal-updates :p

---

### Post by OffHand on 2006-08-19
> **WishMaster said:**
> Same here... Didn't have the guts to install the terminal-updates :p

If you have put a # in front of the compiz lines in your list and ran sudo apt-get update you can savely install the updates that come up. I think it is 3 of them. I have installed them myself without a problem. Note: I didn't try a xgl+compiz session yet.

---

### Post by zooounds on 2006-08-21
I've applied the fixes above but the fonts still look really ugly.

Am I the only one?

---

### Post by WishMaster on 2006-08-23
I must say my fonts still look 'ugly', but there are the same as before (I thought they looked better before :p)
The ugly blurry bold is gone now, and aMSN displays spaces instead of boxes, so I'm happy

btw: did you reboot?

---

### Post by mmcmonster on 2006-09-10
Does anyone know if it is "safe" yet to re-enable the compiz repositories?

---

### Post by mmcmonster on 2006-09-19
So, has anyone gotten up the courage to reinstate the repository and see if the fonts look okay now?

---

