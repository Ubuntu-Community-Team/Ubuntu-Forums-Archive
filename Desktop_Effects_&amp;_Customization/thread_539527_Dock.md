---
title: "Dock"
date: 2007-08-31
forum: Desktop Effects &amp; Customization
---

### Post by kennster on 2007-08-31
ware is a good dock ?? i miss mine off my mac book and want it on here i had one on vista then i made the switch and havent been able to find one for ubuntu plz give me a link or to im running berly if it has one tell me how to bring it up

---

### Post by Inxsible on 2007-08-31
> **kennster said:**
> ware is a good dock ?? i miss mine off my mac book and want it on here i had one on vista then i made the switch and havent been able to find one for ubuntu plz give me a link or to im running berly if it has one tell me how to bring it up

There are a lot of choices.

1) AWN
2) KibaDock
3) KoolDock
4) gDesklet Dock
5) SimDock

Search the forums, there are a LOT of posts regarding installation of anyone of these.

---

### Post by Steve1961 on 2007-08-31
> **kennster said:**
> ware is a good dock ?? i miss mine off my mac book and want it on here i had one on vista then i made the switch and havent been able to find one for ubuntu plz give me a link or to im running berly if it has one tell me how to bring it up

see this thread:

[http://ubuntuforums.org/showthread.php?t=385981&highlight=avant](http://ubuntuforums.org/showthread.php?t=385981&highlight=avant)

---

### Post by Bart_D on 2007-08-31
Are these the steps for installing AWN?

Download
=========
There are no new releases as yet, if you would like to build from the current source, run:

$ bzr co [http://bazaar.launchpad.net/~awn-core/awn/trunk](http://bazaar.launchpad.net/~awn-core/awn/trunk) avant-window-navigator
$ cd avant-window-navigator
$ ./autogen.sh && make && sudo make install

---

### Post by Steve1961 on 2007-08-31
> **Bart_D said:**
> Are these the steps for installing AWN?

Download
=========
There are no new releases as yet, if you would like to build from the current source, run:

$ bzr co [http://bazaar.launchpad.net/~awn-core/awn/trunk](http://bazaar.launchpad.net/~awn-core/awn/trunk) avant-window-navigator
$ cd avant-window-navigator
$ ./autogen.sh && make && sudo make install

I don't use this myself, but looks to me as if you just need to add the repos and then install the packages in the usual way.  If you prefer, you can build your own as suggested

---

### Post by FuturePilot on 2007-08-31
You could do it that way, but I think it would be easier if you added a repo (there is one floating around here somewhere for AWN) and installed it that way. Then you will also be kept up-to-date when ever a new version is released.
These repos```
deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
```
```
sudo apt-get update
sudo apt-get install avant-window-navigator-bzr
```

---

### Post by Bart_D on 2007-08-31
1.  Hey, thanks a lot, will give it a crack.  What would be my next step after entering the above code?  I mean how do I get it to show up on the desktop because I've read too many horror stories on these forums?  Is there a SAFE sequence of "clicks" that I could follow to ensure that it is up and running properly?  I've got compiz-fusion running on srtartup.

2.  If I have to, how would I uninstall it?

---

### Post by FuturePilot on 2007-08-31
You should be able to just go Applications>Accessories>Avant Window Navigator
If you would need to uninstall just do
```
sudo apt-get remove avant-window-navigator-bzr
```

---

### Post by Inxsible on 2007-09-01
FuturePilot, I tried this repo, but it also want to install a bunch of beryl stuff like beryl, beryl-core beryl-plugins etc...I already run Compiz Fusion and i dont want beryl. how do i tell it that I already have CF ?

---

### Post by FuturePilot on 2007-09-01
Do you still have Beryl installed from the Ubuntu repos? I remember when I added that one I had Beryl installed and it wanted to update it.

---

### Post by Inxsible on 2007-09-01
> **FuturePilot said:**
> Do you still have Beryl installed from the Ubuntu repos? I remember when I added that one I had Beryl installed and it wanted to update it.
No I don't have Beryl installed.

```
locate *beryl*
``` gives this```
/usr/share/app-install/desktop/beryl-manager.desktop
/usr/share/app-install/desktop/beryl-settings.desktop
/usr/share/app-install/desktop/beryl-settings-simple.desktop
/home/inxsible/.icons/Aero-stlxv/64x64/apps/beryl-manager.png
/home/inxsible/.icons/Aero-stlxv/128x128/apps/beryl-manager.png
/home/inxsible/.icons/Aero-stlxv/24x24/apps/beryl-manager.png
/home/inxsible/.icons/Aero-stlxv/48x48/apps/beryl-manager.png
/home/inxsible/.icons/Aero-stlxv/96x96/apps/beryl-manager.png
/home/inxsible/.icons/Aero-stlxv/scalable/apps/beryl-manager.png
/home/inxsible/.icons/Aero-stlxv/72x72/apps/beryl-manager.png
/home/inxsible/.icons/Aero-stlxv/22x22/apps/beryl-manager.png
/home/inxsible/.icons/Aero-stlxv/32x32/apps/beryl-manager.png
/home/inxsible/.icons/Aero-stlxv/36x36/apps/beryl-manager.png
/home/inxsible/.icons/Aero-stlxv/16x16/apps/beryl-manager.png

```As you can see, they are only png files from a theme that I have and 3 are .desktop files.

---

### Post by FuturePilot on 2007-09-01
Would you happen to be using aptitude to install it?

---

### Post by Bart_D on 2007-09-01
> **FuturePilot said:**
> You could do it that way, but I think it would be easier if you added a repo (there is one floating around here somewhere for AWN) and installed it that way. Then you will also be kept up-to-date when ever a new version is released.
These repos```
deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
```
```
sudo apt-get update
sudo apt-get install avant-window-navigator-bzr
```

Ok, I've just tried this but it's not working.  I entered those 2 deb lines in the terminal and it said deb: bash: not recognized.  Do I need to enter them in Synaptic>Settings>Repositories, Reload and thene enter the other 2 lines in a terminal?  I;'m new to this..sorry.

What am I missing?

---

### Post by Inxsible on 2007-09-01
> **Bart_D said:**
> Ok, I've just tried this but it's not working.  I entered those 2 deb lines in the terminal and it said deb: bash: not recognized.  Do I need to enter them in Synaptic>Settings>Repositories, Reload and thene enter the other 2 lines in a terminal?  I;'m new to this..sorry.

What am I missing?
umm...you have to add those deb lines in your sources.list

```
gksudo gedit /etc/apt/sources.list
```Then add these lines to the end of the file ```

deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
```

then back in the terminal do ```
sudo apt-get update && sudo apt-get install avant-window-navigator-bzr
```

---

### Post by Inxsible on 2007-09-01
> **FuturePilot said:**
> Would you happen to be using aptitude to install it?

d'oh #-o  I am so used to aptitude that I forgot it installs all dependencies too !!

Also, the fact that it was 3 am in the morning could have played a part in it. :D

---

### Post by hidden_leaf_sasuke on 2007-09-01
do some research, pick the best dock for you, install it and enjoy..:)

---

### Post by Bart_D on 2007-09-02
> **Inxsible said:**
> umm...you have to add those deb lines in your sources.list

```
gksudo gedit /etc/apt/sources.list
```Then add these lines to the end of the file ```

deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
```

then back in the terminal do ```
sudo apt-get update && sudo apt-get install avant-window-navigator-bzr
```

Worked.  Thanks for the help.

---

### Post by kennster on 2007-09-02
worked for me to BUT i click on the icon nuthing happens to start it up....

---

### Post by Inxsible on 2007-09-02
> **kennster said:**
> worked for me to BUT i click on the icon nuthing happens to start it up....
What icon ?

AWN or AWN Manager ?

---

### Post by kennster on 2007-09-03
i know ive seen this on here be for sry i cant find it but any way im running AWN and whell when i run it about an inch or 2 of the bottom of my screen goes black and the dock pops up and it stays black till i close the program.... any ideas it worked fine it just started doing this .... 40min ago when i changed it for a 2d dock to a more 3d one .... i tryed changeing it back didnt work

---

### Post by FuturePilot on 2007-09-03
You need to be running some type of compositing like Beryl or Compiz or Compiz Fusion.

---

