---
title: "XFCE 4.2 now in hoary!"
date: 2005-04-02
forum: Desktop Environments
---

### Post by taygan on 2005-04-02
hooray, xfce 4.2 finally made it into hoary universe!

I had one issue switching from os-cillation repositories to ubuntu hoary repositories.

a broken pipe in python2.4-exo0.3 as it tried to overwrite files from python2.3-exo0.3


solution:

uninstall python2.3-exo0.3 and python-exo0.3

then install python2.4-exo0.3 and reinstall python-exo0.3

Now you're set to go!

---

### Post by operato on 2005-04-03
i installed xfce4.2 and it's broke the right-click menu with an error: 

** (xfdesktop:7331): CRITICAL **: XfceDesktopMenu init failed (The XfceDesktopMenu module could not be loaded: /usr/lib/xfce4/modules/xfce4_desktop_menu.so: undefined symbol: quit)

** (xfdesktop:7331): WARNING **: xfdesktop: Unable to initialise menu module. Right-click menu will be unavailable.

anyone know what's up with that?

---

### Post by ubuntu_demon on 2005-04-03
I just installed xfce4 it's very nice and fast.

It has also a very bloated start menu :( What I mean by this is that I have an enormous applications menu , an openoffice menu that isn't part of the office menu, I don't have a games menu , I direct links to terminal,webbrowser and filemanager that I already have in my panel.

how do I configure xfce to use esound ?

xfce 4 menu editor doesn't work :(

edit :
apparantly it was the middle mouse button menu editor :)
I still have to find a way to edit the menu though.

---

### Post by crimsun on 2005-04-03
[QUOTE=operato]i installed xfce4.2 and it's broke the right-click menu with an error: 

** (xfdesktop:7331): CRITICAL **: XfceDesktopMenu init failed (The XfceDesktopMenu module could not be loaded: /usr/lib/xfce4/modules/xfce4_desktop_menu.so: undefined symbol: quit)

** (xfdesktop:7331): WARNING **: xfdesktop: Unable to initialise menu module. Right-click menu will be unavailable.

anyone know what's up with that?[/QUOTE]
Fixed in the latest update; packages should be available in 3 hours.

---

### Post by bored2k on 2005-04-03
[QUOTE=demon666_nl]I just installed xfce4 it's very nice and fast.

It has also a very bloated start menu :( What I mean by this is that I have an enormous applications menu , an openoffice menu that isn't part of the office menu, I don't have a games menu , I direct links to terminal,webbrowser and filemanager that I already have in my panel.

how do I configure xfce to use esound ?

xfce 4 menu editor doesn't work :(

edit :
apparantly it was the middle mouse button menu editor :)
I still have to find a way to edit the menu though.[/QUOTE]
 From a terminal type
esd &

You'll hear a strange sound.

---

### Post by ubuntu_demon on 2005-04-04
bore2k : thnx

I created a new xfce menu. It's a little less bloated by default. I've also removed all kde packages I had installed (I wasn't using them at the moment anyway)) this helped a little again.

I still want to move my openoffice menu into the office menu. 

I've tried some things and now I have a debian menu in my xfce menu :-s

**edit :**
with a bit of playing (looking for menu.xdg files and removing my .local and .config directories I managed to clean up my applications sub-menu) But I still have to remove the debian menu and move the openoffice menu into the office menu. The debian menu is easy I just forgot the var/lib/menu.xdg (or something) stuff.

---

### Post by ubuntu_demon on 2005-04-04
I've played enough with xfce4 to feel confident to use it as my only desktop-environment on my internet gateway/fileserver (using xfwm4 and vncserver

It's install size is only 755 mb. I downgraded my ubuntu-base / ubuntu-desktop configuration using debfoster. /home is mounted on a different partition.

I've also got installed J2SE and hugin lite.

this is my /var/lib/debfoster/keepers :

```

amule
cgoban
debfoster
deborphan
firestarter
flashplayer-mozilla
gaim
gnugo
grub
grubconf
isag
linux-686
mozilla-firefox
nmap
prelink
python
raidtools2
samba
slocate
smbfs
ssh
swf-player
ubuntu-base
unrar
vncserver
xdiskusage
xfce4
xfce4-goodies
xfwm4
xserver-xorg

```

I have no more problems with xfce4 at the moment.

---

### Post by bored2k on 2005-04-04
XFCE-Hoary still won't let me configure my video resolution :( *bad boy~* ..

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=bored2k]XFCE-Hoary still won't let me configure my video resolution :( *bad boy~* ..[/QUOTE]
 Have you tried sudo dpkg-reconfigure xfce4 ?
how do you like xfce apart from this issue ? What system do you run xfce4 on ?

---

### Post by bored2k on 2005-04-04
[QUOTE=demon666_nl]Have you tried sudo dpkg-reconfigure xfce4 ?
how do you like xfce apart from this issue ? What system do you run xfce4 on ?[/QUOTE]
 On warty I was a XFCE 4.2/GNOME 2,8 user, so yes I liked it, specially it speed. I haven't tried that one, gonna try it as son as I click send message. It's my custom ***noir***, p4 2.4ghz, crappy SiS 661fx.

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=bored2k]On warty I was a XFCE 4.2/GNOME 2,8 user, so yes I liked it, specially it speed. I haven't tried that one, gonna try it as son as I click send message. It's my custom ***noir***, p4 2.4ghz, crappy SiS 661fx.[/QUOTE]
 Did you already try to reconfigure your xserver using sudo dpkg-reconfigure xserver-xorg (that one was too trivial for me to mention I'm sorry)

Now that I'm getting used to xfce4 I'm liking it very much especially :
- it looks good
- it's fast
- no unnecessary services are running
- gnome applications look native

My workstation is fast enough to not notice the difference between gnome and xfce so I have returned to gnome on that one for the time being. I'm sure I'll play with other windowmanagers on it.Playing with stuff shouldn't be done on a server right? :)

---

### Post by bored2k on 2005-04-04
[QUOTE=demon666_nl]Did you already try to reconfigure your xserver using sudo dpkg-reconfigure xserver-xorg (that one was too trivial for me to mention I'm sorry)

Now that I'm getting used to xfce4 I'm liking it very much especially :
- it looks good
- it's fast
- no unnecessary services are running
- gnome applications look native

My workstation is fast enough to not notice the difference between gnome and xfce so I have returned to gnome on that one for the time being. I'm sure I'll play with other windowmanagers on it.Playing with stuff shouldn't be done on a server right? :)[/QUOTE]
 Didn't work. But I found a solution for now:
apt-get remove xfce [and all its packages].

I'll have to start retrying other environments like blackbox and such -no matter how much I like gnome, I'm a speed freak, if I find something that can be used daily while not being as ugly as a shell window, I'm all love for it [and nothing related to KDE :roll:] .

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=bored2k]Didn't work. But I found a solution for now:
apt-get remove xfce [and all its packages].

I'll have to start retrying other environments like blackbox and such -no matter how much I like gnome, I'm a speed freak, if I find something that can be used daily while not being as ugly as a shell window, I'm all love for it [and nothing related to KDE :roll:] .[/QUOTE]
 don't give up just now that's too easy :)

1) you had apparently installed the meta-package xfce instead of the package xfce4. This is wrong. Go correct it! :)

2)You can also do like me and remove almost everything from ubunt-desktop including gdm and make xfwm4 the default wm. debfoster rules for a system clean up.

---

### Post by bored2k on 2005-04-04
[QUOTE=demon666_nl]don't give up just now that's too easy :)

1) you had apparently installed the meta-package xfce instead of the package xfce4. This is wrong. Go correct it! :)

2)You can also do like me and remove almost everything from ubunt-desktop including gdm and make xfwm4 the default wm. debfoster rules for a system clean up.[/QUOTE]
 Before I remove everything I have to make sure xfce will work ..
and I have never used debfoster [*mommy I'm scared :-$*].

I think I'm positive about installing xfce4 package, but I'll retry just for the heck of it.

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=bored2k]Before I remove everything I have to make sure xfce will work ..
and I have never used debfoster [*mommy I'm scared :-$*].

I think I'm positive about installing xfce4 package, but I'll retry just for the heck of it.[/QUOTE]
 first install xfce4 instead of xfce and try if this fixes your problem.

But if you copy my debfoster keepers file and modify it a little nothing could happen .. in the worst case you won't get a working xfce4 but have to install ubuntu-desktop again (which should be in apt's cache then)

PS I really really like how xfce runs on my gateway!

I'm going to sleep ... probably will see you on the forums tomorrow :-D

---

### Post by bored2k on 2005-04-04
[QUOTE=demon666_nl]first install xfce4 instead of xfce and try if this fixes your problem.

But if you copy my debfoster keepers file and modify it a little nothing could happen .. in the worst case you won't get a working xfce4 but have to install ubuntu-desktop again (which should be in apt's cache then)

PS I really really like how xfce runs on my gateway!

I'm going to sleep ... probably will see you on the forums tomorrow :-D[/QUOTE]
 Aight TTYL dude. BTW, it still didn't work, download E, Blackbox, Fbox as we speak :-P.

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=bored2k]Aight TTYL dude. BTW, it still didn't work, download E, Blackbox, Fbox as we speak :-P.[/QUOTE]
 np :)

I would go for xfce4 though. I didn't expect much but now that I use it I really really like it. It's so lean,mean and clean but at the same time very usable,freedesktop compliance and good gnome integration!

PS the hoary package xfce is the 3.8.x version. 

I'm really going to sleep now ... only 4 hours left.

bye for now :-D

**edit**
you should try sysstat / isag for performance evaluation so you can compare between the different environments

---

