---
title: "HOWTO: Painless Compiz Fusion on Feisty"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by reacocard on 2007-07-05
I have backported compiz fusion from gutsy and placed it in a repo. In my testing, these packages have been more stable than Trevinos, while still offering most of the same functionality.

NOTE: These packages are for 32-bit only.

WARNING: Make sure beryl is removed/disabled first, it'll conflict with this guide if its enabled. Feisty's built-in Desktop Effects are fine though.
WARNING: IF your are using Trevino's eyecandy repo, do not use this guide without COMPLETELY removing his repo and all packages from it first.

_**[SIZE="3"]Guide:[/SIZE]**_

Add this to your /etc/apt/sources.list:
```
deb http://download.tuxfamily.org/syzygy42 feisty compiz
deb-src http://download.tuxfamily.org/syzygy42 feisty compiz
```

Then do this in a terminal:
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg 
sudo apt-key add 8434D43A.gpg
rm 8434D43A.gpg
sudo apt-get update
sudo apt-get upgrade
```

And finally, this:
```
sudo apt-get install compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-plugins compizconfig-settings-manager desktop-effects
```

That's it, just log out/in (make sure desktop effects are enabled!) and compiz fusion will start.

---

### Post by orb9220 on 2007-07-05
Nice info thanks but does it take care of removing Beryl too?

---

### Post by reacocard on 2007-07-05
> **orb9220 said:**
> Nice info thanks but does it take care of removing Beryl too?

No, because I can't predict whether you have it or not. This guide is designed with a normal feisty install in mind.

Really, you don't need to *remove* beryl, just disable it by removing it from your startup programs.

---

### Post by dannyboy79 on 2007-07-05
You should have them remove compiz first, then update the sources.list, then do an update, then do an install. Without the update, it will keep failing!!!

I would also strongly suggest you inform people that they should remove the trevino's git repo's also. How often will you backport the compiz from Gutsy? Why would anyone want to use this when trevino's repo is a GIT repo, which is being developed, worked on, and updated daily and sometimes 2 times a day?

---

### Post by reacocard on 2007-07-05
> **dannyboy79 said:**
> You should have them remove compiz first, then update the sources.list, then do an update, then do an install. Without the update, it will keep failing!!!

I would also strongly suggest you inform people that they should remove the trevino's git repo's also. How often will you backport the compiz from Gutsy? Why would anyone want to use this when trevino's repo is a GIT repo, which is being developed, worked on, and updated daily and sometimes 2 times a day?

Very good advice, I'll update the guide right now. I'll backport whenever it updates in gutsy (and I check, is there an RSS feed for this or something? EDIT: found the gutsy-changes mailing list), and as I said, in my experience these are more stable than Trevino's. Trevino's were crashing 2-3 times per day for me, but these have yet to crash.

---

### Post by dannyboy79 on 2007-07-05
ok, I wasn't trying to say that your repo was a bad thing, I was merely wanting to point out to other's the advantage of using your repo versus using trevino's repo. Thank you for the guide, it's very easy to follow and do. Since you're saying you're experiencing way less crashing, I'll give it a try. thanks again.

---

### Post by BlahMan_of.Doom on 2007-07-05
I tried this guide too, but the cube still does NOT work. :(

---

### Post by dannyboy79 on 2007-07-05
I have a weird occurance with rotating the 3D cube myself as well. what if you open any app, like a terminal for instance, now when you hold ctrl+alt and hold the left mouse button to rotate the cube, make sure the mouse cursor is actually on the apps window you just opened. That's the only way I can get my rotate cube 3D to work within my first display, the odd thing is that it works fine on my second display on the main desktop without any apps open or windows open?

Try that, see if that works for you. Here's a picture of what I mean.

[http://img112.imageshack.us/img112/8816/untitled2ft3.png](http://img112.imageshack.us/img112/8816/untitled2ft3.png)


 Despite the picture being windows, just imagine that the arrow I circled is your mouse cursor, then try to hold ctrl+alt+and the left mouse button then move mouse left or right and your 3d cube should rotate. otherwise, you can hold ctrl+alt then arrow left or right and that'll rotate the cube, to move the active window to a new cube side, hold ctrl+alt+shift then hit left or right arrow.

---

### Post by vishnu on 2007-07-05
everything works for me but the active windows tend to dock to the panels or side of the screen and get stuck and I have to pull them away.  Aside from holding down Ctrl how can I fix this.
I have 3D effects installed and GL Desktop (gnome-compiz-manager) and I see no options to turn this off.

---

### Post by reacocard on 2007-07-10
I've backported a newer set of debs and updated the guide, enjoy!

---

### Post by Absorbed on 2007-07-10
It was all going swimmingly until I typed in the final command:

```
mark@virbius:~$ sudo apt-get install compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-plugins compizconfig-settings-manager desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
desktop-effects is already the newest version.
The following extra packages will be installed:
  compiz compiz-gnome libcompizconfig-backend-gconf libcompizconfig0
  python-compizconfig
Suggested packages:
  nvidia-glx
The following packages will be REMOVED
  compiz-gtk
The following NEW packages will be installed
  compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compizconfig-settings-manager libcompizconfig-backend-gconf libcompizconfig0
  python-compizconfig
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins
4 upgraded, 6 newly installed, 1 to remove and 0 not upgraded.
Need to get 2044kB of archives.
After unpacking 7344kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://download.tuxfamily.org feisty/compiz compiz-plugins 1:0.5.1+git20070703-0ubuntu3 [272kB]
Get: 2 http://download.tuxfamily.org feisty/compiz compiz-gnome 1:0.5.1+git20070703-0ubuntu3 [165kB]
Get: 3 http://download.tuxfamily.org feisty/compiz compiz 1:0.5.1+git20070703-0ubuntu3 [28.8kB]
Get: 4 http://download.tuxfamily.org feisty/compiz compiz-core 1:0.5.1+git20070703-0ubuntu3 [331kB]
Get: 5 http://download.tuxfamily.org feisty/compiz libcompizconfig0 0.0+git20070626-0ubuntu1 [50.2kB]
Get: 6 http://download.tuxfamily.org feisty/compiz libcompizconfig-backend-gconf 0.0+git20070620-0ubuntu1 [30.3kB]
Get: 7 http://download.tuxfamily.org feisty/compiz compiz-fusion-plugins-main 0.0.0+git20070703-0ubuntu3 [394kB]
Get: 8 http://download.tuxfamily.org feisty/compiz compiz-fusion-plugins-extra 0.0.0+git20070703-0ubuntu3 [225kB]
Get: 9 http://download.tuxfamily.org feisty/compiz python-compizconfig 0.0.0+git20070703-0ubuntu2 [102kB]
Get: 10 http://download.tuxfamily.org feisty/compiz compizconfig-settings-manager 0.0+git20070703-0ubuntu2 [445kB]
Fetched 2043kB in 1m9s (29.4kB/s)                                              
Failed to fetch http://download.tuxfamily.org/syzygy42/pool/feisty/compiz/libcompizconfig-backend-gconf_0.0+git20070620-0ubuntu1_i386.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

It seems to be a problem with the source.

---

### Post by gururise on 2007-07-10
> **Absorbed said:**
> It was all going swimmingly until I typed in the final command:

It seems to be a problem with the source.
Help! Same problem here!

---

### Post by reacocard on 2007-07-10
Sorry guys, my bad. Should be fixed now.

---

### Post by Absorbed on 2007-07-10
Works :)

---

### Post by dxdemetriou on 2007-07-20
is still active updated this repo? I ask because there are new packages on gutsy, and to we know if it's going to updated up to the official release of Gutsy.
thanks :)

---

### Post by frenchcr on 2007-07-21
Mine went well until...

```
root@frenchcr02:/etc/apt# sudo apt-get install compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-plugins compizconfig-settings-manager desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwv-1.2-3 libevolution-cil libgsf0.0-cil
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz compiz-gnome libcompizconfig-backend-gconf libcompizconfig0
  libdecoration0 python-compizconfig
The following NEW packages will be installed
  compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-gnome compiz-plugins compizconfig-settings-manager desktop-effects
  libcompizconfig-backend-gconf libcompizconfig0 libdecoration0
  python-compizconfig
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 2194kB of archives.
After unpacking 11.5MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get: 1 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/compiz compiz-core 1:0.5.1+git20070703-0ubuntu3 [331kB]
Get: 2 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/compiz libdecoration0 1:0.5.1+git20070703-0ubuntu3 [45.4kB]
Get: 3 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/compiz compiz-plugins 1:0.5.1+git20070703-0ubuntu3 [272kB]
Get: 4 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/compiz libcompizconfig0 0.0+git20070626-0ubuntu1 [50.2kB]
Get: 5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/compiz libcompizconfig-backend-gconf 0.0+git20070620-0ubuntu1 [29.3kB]
Get: 6 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/compiz compiz-gnome 1:0.5.1+git20070703-0ubuntu3 [165kB]
Get: 7 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/compiz compiz-fusion-plugins-main 0.0.0+git20070711-0ubuntu1 [453kB]
Get: 8 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/compiz compiz 1:0.5.1+git20070703-0ubuntu3 [28.8kB]
Get: 9 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/compiz desktop-effects 0.7.1-0ubuntu5 [47.1kB]
Get: 10 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/compiz compiz-fusion-plugins-extra 0.0.0+git20070703-0ubuntu3 [225kB]
Get: 11 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/compiz python-compizconfig 0.0.0+git20070703-0ubuntu2 [102kB]
Get: 12 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/compiz compizconfig-settings-manager 0.0+git20070703-0ubuntu2 [445kB]
Fetched 2194kB in 2s (786kB/s)                         
Selecting previously deselected package compiz-core.
(Reading database ... 145741 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_1%3a0.5.1+git20070703-0ubuntu3_i386.deb) ...
Selecting previously deselected package libdecoration0.
Unpacking libdecoration0 (from .../libdecoration0_1%3a0.5.1+git20070703-0ubuntu3_i386.deb) ...
Selecting previously deselected package compiz-plugins.
Unpacking compiz-plugins (from .../compiz-plugins_1%3a0.5.1+git20070703-0ubuntu3_i386.deb) ...
Selecting previously deselected package libcompizconfig0.
Unpacking libcompizconfig0 (from .../libcompizconfig0_0.0+git20070626-0ubuntu1_i386.deb) ...
Selecting previously deselected package libcompizconfig-backend-gconf.
Unpacking libcompizconfig-backend-gconf (from .../libcompizconfig-backend-gconf_0.0+git20070620-0ubuntu1_i386.deb) ...
Selecting previously deselected package compiz-gnome.
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.5.1+git20070703-0ubuntu3_i386.deb) ...
Selecting previously deselected package compiz-fusion-plugins-main.
Unpacking compiz-fusion-plugins-main (from .../compiz-fusion-plugins-main_0.0.0+git20070711-0ubuntu1_i386.deb) ...
Selecting previously deselected package compiz.
Unpacking compiz (from .../compiz_1%3a0.5.1+git20070703-0ubuntu3_all.deb) ...
Selecting previously deselected package desktop-effects.
Unpacking desktop-effects (from .../desktop-effects_0.7.1-0ubuntu5_i386.deb) ...
Selecting previously deselected package compiz-fusion-plugins-extra.
Unpacking compiz-fusion-plugins-extra (from .../compiz-fusion-plugins-extra_0.0.0+git20070703-0ubuntu3_i386.deb) ...
Selecting previously deselected package python-compizconfig.
Unpacking python-compizconfig (from .../python-compizconfig_0.0.0+git20070703-0ubuntu2_i386.deb) ...
Selecting previously deselected package compizconfig-settings-manager.
Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.0+git20070703-0ubuntu2_all.deb) ...
Setting up compiz-core (0.5.1+git20070703-0ubuntu3) ...
Setting up libdecoration0 (0.5.1+git20070703-0ubuntu3) ...

Setting up compiz-plugins (0.5.1+git20070703-0ubuntu3) ...
Setting up libcompizconfig0 (0.0+git20070626-0ubuntu1) ...

Setting up libcompizconfig-backend-gconf (0.0+git20070620-0ubuntu1) ...
Setting up compiz-gnome (0.5.1+git20070703-0ubuntu3) ...

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
Setting up compiz-fusion-plugins-main (0.0.0+git20070711-0ubuntu1) ...
Setting up compiz (0.5.1+git20070703-0ubuntu3) ...
Setting up desktop-effects (0.7.1-0ubuntu5) ...

Setting up compiz-fusion-plugins-extra (0.0.0+git20070703-0ubuntu3) ...
Setting up python-compizconfig (0.0.0+git20070703-0ubuntu2) ...
Setting up compizconfig-settings-manager (0.0+git20070703-0ubuntu2) ...
localepurge: Disk space freed in /usr/share/locale: 1096K
root@frenchcr02:/etc/apt# Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!

```


It just sort of hung here...sat for ten minutes...pressed return and it exited back to command line :(

I then went to synaptic and removed compiz and all compiz components (plus desktop effects) and system returned to normal, no damage done.

Anyone spot why it failed :confused: (im sort of new round here...only a few measly beans to my name, proud of them though :)).

---

### Post by dxdemetriou on 2007-07-21
I don't know if I am correct, I think it's something with KDE (are you using KDE)?
Are you using a 32bit computer?
I don't know a lot about KDE, but if you check the names of those errors? what are programs and what packages are from synaptic?
Sorry, I am not very helpful. Maybe somebody else can help..

---

### Post by frenchcr on 2007-07-22
Yes, I am using 32bit and Gnome is my default desktop. I dont have KDE installed at all ( I think the only KDE app I have is Kate text editor). Everything else on my system works tickety-boo.

Im working off a fresh installation, so should have no conflicts.

---

### Post by frenchcr on 2007-07-22
Ok im making a little headway...to get rid of my ksycoca ERROR i simply did this...

```
cd /var/tmp/kdecache-root/ 
cp  kdecache-root  kdecache-root_backup
cd  kdecache-root
rm ksycoca ksycocastamp
```

Then i tried installing compiz and components again (without going through the initial steps..is this wrong)...heres what happened..

```
root@frenchcr02:/home/frenchcr02# sudo apt-get install compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-plugins compizconfig-settings-manager desktop-effectson-plugins-extra compiz-plugins compizconfig-settings-mReading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following extra packages will be installed: 
  compiz compiz-gnome libcompizconfig-backend-gconf libcompizconfig0 libdecoration0 python-compizconfig 
The following NEW packages will be installed 
  compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-settings-manager desktop-effects 
  libcompizconfig-backend-gconf libcompizconfig0 libdecoration0 python-compizconfig 
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B/2194kB of archives. 
After unpacking 11.5MB of additional disk space will be used. 
Do you want to continue [Y/n]? Y 
Selecting previously deselected package compiz-core. 
(Reading database ... 145824 files and directories currently installed.) 
Unpacking compiz-core (from .../compiz-core_1%3a0.5.1+git20070703-0ubuntu3_i386.deb) ... 
Selecting previously deselected package libdecoration0. 
Unpacking libdecoration0 (from .../libdecoration0_1%3a0.5.1+git20070703-0ubuntu3_i386.deb) ... 
Selecting previously deselected package compiz-plugins. 
Unpacking compiz-plugins (from .../compiz-plugins_1%3a0.5.1+git20070703-0ubuntu3_i386.deb) ... 
Selecting previously deselected package libcompizconfig0. 
Unpacking libcompizconfig0 (from .../libcompizconfig0_0.0+git20070626-0ubuntu1_i386.deb) ... 
Selecting previously deselected package libcompizconfig-backend-gconf. 
Unpacking libcompizconfig-backend-gconf (from .../libcompizconfig-backend-gconf_0.0+git20070620-0ubuntu1_i386.deb) ... 
Selecting previously deselected package compiz-gnome. 
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.5.1+git20070703-0ubuntu3_i386.deb) ... 
Selecting previously deselected package compiz-fusion-plugins-main. 
Unpacking compiz-fusion-plugins-main (from .../compiz-fusion-plugins-main_0.0.0+git20070711-0ubuntu1_i386.deb) ... 
Selecting previously deselected package compiz. 
Unpacking compiz (from .../compiz_1%3a0.5.1+git20070703-0ubuntu3_all.deb) ... 
Selecting previously deselected package desktop-effects. 
Unpacking desktop-effects (from .../desktop-effects_0.7.1-0ubuntu5_i386.deb) ... 
Selecting previously deselected package compiz-fusion-plugins-extra. 
Unpacking compiz-fusion-plugins-extra (from .../compiz-fusion-plugins-extra_0.0.0+git20070703-0ubuntu3_i386.deb) ... 
Selecting previously deselected package python-compizconfig. 
Unpacking python-compizconfig (from .../python-compizconfig_0.0.0+git20070703-0ubuntu2_i386.deb) ... 
Selecting previously deselected package compizconfig-settings-manager. 
Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.0+git20070703-0ubuntu2_all.deb) ... 
Setting up compiz-core (0.5.1+git20070703-0ubuntu3) ... 
Setting up libdecoration0 (0.5.1+git20070703-0ubuntu3) ... 

Setting up compiz-plugins (0.5.1+git20070703-0ubuntu3) ... 
Setting up libcompizconfig0 (0.0+git20070626-0ubuntu1) ... 

Setting up libcompizconfig-backend-gconf (0.0+git20070620-0ubuntu1) ... 
Setting up compiz-gnome (0.5.1+git20070703-0ubuntu3) ... 

Setting up compiz-fusion-plugins-main (0.0.0+git20070711-0ubuntu1) ... 
Setting up compiz (0.5.1+git20070703-0ubuntu3) ... 
Setting up desktop-effects (0.7.1-0ubuntu5) ... 

Setting up compiz-fusion-plugins-extra (0.0.0+git20070703-0ubuntu3) ... 
Setting up python-compizconfig (0.0.0+git20070703-0ubuntu2) ... 
Setting up compizconfig-settings-manager (0.0+git20070703-0ubuntu2) ... 
localepurge: Disk space freed in /usr/share/locale: 1096K 
root@frenchcr02:/home/frenchcr02# 
```

I thought SUCCESS!

But when i go to enable desktop effects it doesnt want to do it, plus the radio buttons that used to be in its popup box are gone :confused:

So now ive uninstalled everything compiz and desktop effects, and once again the systems back to normal.

So much for Painless Compiz Fusion on Feisty. This HOWTO seems very much flawed.

---

### Post by reacocard on 2007-07-23
> **dxdemetriou said:**
> is still active updated this repo? I ask because there are new packages on gutsy, and to we know if it's going to updated up to the official release of Gutsy.
thanks :)

It will be updated, I'm just on vacation right now so I only have intermittent internet access. Once I get back I'll get a new set of debs up.

---

### Post by reacocard on 2007-07-23
> **frenchcr said:**
> Ok im making a little headway...to get rid of my ksycoca ERROR i simply did this...

```
cd /var/tmp/kdecache-root/ 
cp  kdecache-root  kdecache-root_backup
cd  kdecache-root
rm ksycoca ksycocastamp
```

Then i tried installing compiz and components again (without going through the initial steps..is this wrong)...heres what happened..

```
root@frenchcr02:/home/frenchcr02# sudo apt-get install compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-plugins compizconfig-settings-manager desktop-effectson-plugins-extra compiz-plugins compizconfig-settings-mReading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following extra packages will be installed: 
  compiz compiz-gnome libcompizconfig-backend-gconf libcompizconfig0 libdecoration0 python-compizconfig 
The following NEW packages will be installed 
  compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-settings-manager desktop-effects 
  libcompizconfig-backend-gconf libcompizconfig0 libdecoration0 python-compizconfig 
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B/2194kB of archives. 
After unpacking 11.5MB of additional disk space will be used. 
Do you want to continue [Y/n]? Y 
Selecting previously deselected package compiz-core. 
(Reading database ... 145824 files and directories currently installed.) 
Unpacking compiz-core (from .../compiz-core_1%3a0.5.1+git20070703-0ubuntu3_i386.deb) ... 
Selecting previously deselected package libdecoration0. 
Unpacking libdecoration0 (from .../libdecoration0_1%3a0.5.1+git20070703-0ubuntu3_i386.deb) ... 
Selecting previously deselected package compiz-plugins. 
Unpacking compiz-plugins (from .../compiz-plugins_1%3a0.5.1+git20070703-0ubuntu3_i386.deb) ... 
Selecting previously deselected package libcompizconfig0. 
Unpacking libcompizconfig0 (from .../libcompizconfig0_0.0+git20070626-0ubuntu1_i386.deb) ... 
Selecting previously deselected package libcompizconfig-backend-gconf. 
Unpacking libcompizconfig-backend-gconf (from .../libcompizconfig-backend-gconf_0.0+git20070620-0ubuntu1_i386.deb) ... 
Selecting previously deselected package compiz-gnome. 
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.5.1+git20070703-0ubuntu3_i386.deb) ... 
Selecting previously deselected package compiz-fusion-plugins-main. 
Unpacking compiz-fusion-plugins-main (from .../compiz-fusion-plugins-main_0.0.0+git20070711-0ubuntu1_i386.deb) ... 
Selecting previously deselected package compiz. 
Unpacking compiz (from .../compiz_1%3a0.5.1+git20070703-0ubuntu3_all.deb) ... 
Selecting previously deselected package desktop-effects. 
Unpacking desktop-effects (from .../desktop-effects_0.7.1-0ubuntu5_i386.deb) ... 
Selecting previously deselected package compiz-fusion-plugins-extra. 
Unpacking compiz-fusion-plugins-extra (from .../compiz-fusion-plugins-extra_0.0.0+git20070703-0ubuntu3_i386.deb) ... 
Selecting previously deselected package python-compizconfig. 
Unpacking python-compizconfig (from .../python-compizconfig_0.0.0+git20070703-0ubuntu2_i386.deb) ... 
Selecting previously deselected package compizconfig-settings-manager. 
Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.0+git20070703-0ubuntu2_all.deb) ... 
Setting up compiz-core (0.5.1+git20070703-0ubuntu3) ... 
Setting up libdecoration0 (0.5.1+git20070703-0ubuntu3) ... 

Setting up compiz-plugins (0.5.1+git20070703-0ubuntu3) ... 
Setting up libcompizconfig0 (0.0+git20070626-0ubuntu1) ... 

Setting up libcompizconfig-backend-gconf (0.0+git20070620-0ubuntu1) ... 
Setting up compiz-gnome (0.5.1+git20070703-0ubuntu3) ... 

Setting up compiz-fusion-plugins-main (0.0.0+git20070711-0ubuntu1) ... 
Setting up compiz (0.5.1+git20070703-0ubuntu3) ... 
Setting up desktop-effects (0.7.1-0ubuntu5) ... 

Setting up compiz-fusion-plugins-extra (0.0.0+git20070703-0ubuntu3) ... 
Setting up python-compizconfig (0.0.0+git20070703-0ubuntu2) ... 
Setting up compizconfig-settings-manager (0.0+git20070703-0ubuntu2) ... 
localepurge: Disk space freed in /usr/share/locale: 1096K 
root@frenchcr02:/home/frenchcr02# 
```

I thought SUCCESS!

But when i go to enable desktop effects it doesnt want to do it, plus the radio buttons that used to be in its popup box are gone :confused:

So now ive uninstalled everything compiz and desktop effects, and once again the systems back to normal.

So much for Painless Compiz Fusion on Feisty. This HOWTO seems very much flawed.

The radio buttons disappearing is supposed to happen, the gutsy desktop effects doesn't have them either. Did you log out/in after doing this? If not, try that, it may help. If that does not work, do a 'compiz --replace' in a terminal and post the output here.

---

### Post by frenchcr on 2007-07-23
"The radio buttons disappearing is supposed to happen, the gutsy desktop effects doesn't have them either. Did you log out/in after doing this? If not, try that, it may help. If that does not work, do a 'compiz --replace' in a terminal and post the output here"



I uninstalled everything and went back through your guide step by step. I enabled desktop effects, and then when i closed the desktop effects window it did something fancy :) , i.e. it seemed to work for a moment. So i logged out as you asked. I had a quick look in sessions for anything new as i remember with beryl you used to select a different type of session, but there was just the usual. So i changed nothing and logged in as normal but no luck :(  ....

heres what happened when i typed the command compiz --replace

```
root@frenchcr02:/home/frenchcr02# compiz --replace
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)
Adding plugin fs (fs)
Adding plugin cube (cube)
Adding plugin extrawm (extrawm)
Adding plugin group (group)
Adding plugin firepaint (firepaint)
Adding plugin cubereflex (cubereflex)
Adding plugin annotate (annotate)
Adding plugin crashhandler (crashhandler)
Adding plugin water (water)
Adding plugin text (text)
Adding plugin thumbnail (thumbnail)
Adding plugin switcher (switcher)
Adding plugin png (png)
Adding plugin bench (bench)
Adding plugin mblur (mblur)
Adding plugin trailfocus (trailfocus)
Adding plugin video (video)
Adding plugin zoom (zoom)
Adding plugin addhelper (addhelper)
Adding plugin glib (glib)
Adding plugin animation (animation)
Adding plugin wobbly (wobbly)
Adding plugin reflex (reflex)
Adding plugin opacify (opacify)
Adding plugin put (put)
Adding plugin clone (clone)
Adding plugin resizeinfo (resizeinfo)
Adding plugin wall (wall)
Adding plugin dbus (dbus)
Adding plugin resize (resize)
Adding plugin rotate (rotate)
Adding plugin vpswitch (vpswitch)
Adding plugin scale (scale)
Adding plugin inotify (inotify)
Adding plugin showdesktop (showdesktop)
Adding core settings (General Options)
Adding plugin place (place)
Adding plugin winrules (winrules)
Adding plugin neg (neg)
Adding plugin snap (snap)
Adding plugin blur (blur)
Adding plugin minimize (minimize)
Adding plugin ring (ring)
Adding plugin imgjpeg (imgjpeg)
Adding plugin svg (svg)
Adding plugin scaleaddon (scaleaddon)
Adding plugin splash (splash)
Adding plugin decoration (decoration)
Adding plugin fade (fade)
Adding plugin regex (regex)
Adding plugin move (move)
Adding plugin fadedesktop (fadedesktop)
Adding plugin expo (expo)
Adding plugin screenshot (screenshot)
Adding plugin plane (plane)
Backend     : gconf
Integration : true
Profile     : default
Initializing core options...done
Initializing switcher options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing zoom options...done
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
Initializing resize options...done
Initializing place options...done
Initializing neg options...done
Initializing svg options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
Initializing move options...done
Initializing expo options...done
Initializing animation options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
Segmentation fault (core dumped)



```

the computer seemed to hang here, so I rebooted.

---

### Post by reacocard on 2007-07-24
> **frenchcr said:**
> "The radio buttons disappearing is supposed to happen, the gutsy desktop effects doesn't have them either. Did you log out/in after doing this? If not, try that, it may help. If that does not work, do a 'compiz --replace' in a terminal and post the output here"



I uninstalled everything and went back through your guide step by step. I enabled desktop effects, and then when i closed the desktop effects window it did something fancy :) , i.e. it seemed to work for a moment. So i logged out as you asked. I had a quick look in sessions for anything new as i remember with beryl you used to select a different type of session, but there was just the usual. So i changed nothing and logged in as normal but no luck :(  ....

heres what happened when i typed the command compiz --replace

```
root@frenchcr02:/home/frenchcr02# compiz --replace
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:27063): Wnck-WARNING **: Unhandled action type (nil)
Adding plugin fs (fs)
Adding plugin cube (cube)
Adding plugin extrawm (extrawm)
Adding plugin group (group)
Adding plugin firepaint (firepaint)
Adding plugin cubereflex (cubereflex)
Adding plugin annotate (annotate)
Adding plugin crashhandler (crashhandler)
Adding plugin water (water)
Adding plugin text (text)
Adding plugin thumbnail (thumbnail)
Adding plugin switcher (switcher)
Adding plugin png (png)
Adding plugin bench (bench)
Adding plugin mblur (mblur)
Adding plugin trailfocus (trailfocus)
Adding plugin video (video)
Adding plugin zoom (zoom)
Adding plugin addhelper (addhelper)
Adding plugin glib (glib)
Adding plugin animation (animation)
Adding plugin wobbly (wobbly)
Adding plugin reflex (reflex)
Adding plugin opacify (opacify)
Adding plugin put (put)
Adding plugin clone (clone)
Adding plugin resizeinfo (resizeinfo)
Adding plugin wall (wall)
Adding plugin dbus (dbus)
Adding plugin resize (resize)
Adding plugin rotate (rotate)
Adding plugin vpswitch (vpswitch)
Adding plugin scale (scale)
Adding plugin inotify (inotify)
Adding plugin showdesktop (showdesktop)
Adding core settings (General Options)
Adding plugin place (place)
Adding plugin winrules (winrules)
Adding plugin neg (neg)
Adding plugin snap (snap)
Adding plugin blur (blur)
Adding plugin minimize (minimize)
Adding plugin ring (ring)
Adding plugin imgjpeg (imgjpeg)
Adding plugin svg (svg)
Adding plugin scaleaddon (scaleaddon)
Adding plugin splash (splash)
Adding plugin decoration (decoration)
Adding plugin fade (fade)
Adding plugin regex (regex)
Adding plugin move (move)
Adding plugin fadedesktop (fadedesktop)
Adding plugin expo (expo)
Adding plugin screenshot (screenshot)
Adding plugin plane (plane)
Backend     : gconf
Integration : true
Profile     : default
Initializing core options...done
Initializing switcher options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing zoom options...done
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
Initializing resize options...done
Initializing place options...done
Initializing neg options...done
Initializing svg options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
Initializing move options...done
Initializing expo options...done
Initializing animation options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
Segmentation fault (core dumped)



```

the computer seemed to hang here, so I rebooted.

looks like your graphics card doesn't have the GLX extension compiz wants. Beryl is currently better at detecting these things and working around them than compiz is, so I would say to just stay with beryl for now. You could try adding the --indirect-rendering option to 'compiz --replace' and see if that helps, but if it doesn't I have no idea how to fix this.

---

### Post by dannyboy79 on 2007-07-24
try changing your default depth from 32 to 24 within your xorg.conf.

---

### Post by scottylans on 2007-07-31
I followed the directions at the start of this and all they did was hose my install of 7.04 - awesome :/

Everything now has a 2mm thick white border around it and I still have the graphical glitches on my screen from the Dell 8600 bug.

I came to this thread due to the this post here 
[http://ubuntuforums.org/showthread.php?t=506390](http://ubuntuforums.org/showthread.php?t=506390)

On top of having a white border around windows, my network manager disapeared, so no more WPA for me :/

Back to Windows I go, again :(
I've been trying to use Ubuntu with WPA and kismet (2 cards, one system) since 5.04 - I've never once had it work properly always something breaks.

---

### Post by scottylans on 2007-07-31
I have created a thread outlining my problems here .
[http://ubuntuforums.org/showthread.php?p=3109513#post3109513](http://ubuntuforums.org/showthread.php?p=3109513#post3109513)

---

### Post by pdarkness on 2007-08-16
I must admit I started here spent a day or two and now I have 3 computer all with Feisty and compiz fusion working I picked up a trick here and a trick there but I must say the most help and packets I'm using I got from 
[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

gl to you all and just remember that if you just work on it it's gona work in the end ^-^

p.s I also found it much better to use emerald

and the command for starting compiz with emerald is
compiz --replace -c emerald

you should have seen the smile on my face when it worked the first time :P

---

