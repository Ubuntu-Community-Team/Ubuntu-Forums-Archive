---
title: "cant install racer"
date: 2006-10-25
forum: Gaming &amp; Leisure
---

### Post by qrm on 2006-10-25
Hi!

Ive downloaded couple of versions of racer (beta and non-beta) and I cant seem to get them installed. When I try to open the installer it opens but in the terminal are couple of error messages:'
```
Gtk-WARNING **: Failed to load module "libgail.so": libgail.so: cannot open shared object file: No such file or directory

Gtk-WARNING **: Failed to load module "libatk-bridge.so": libatk-bridge.so: cannot open shared object file: No such file or directory

Gdk-WARNING **: locale not supported by C library

```

The installer fires up but i cant click on the base install square, it just wont go "down" I can still click every other button. Screenshot:

[[IMG]http://img104.imageshack.us/img104/5623/screenshot6uz3.png[/IMG]](http://imageshack.us)

Ive installed everything that looks even remotely like libgail and libatk. all the help is appreciated

---

### Post by Perfect Storm on 2006-10-25
Do you have libgail and libatk installed?

Edit: doh, didn't see ya last comment under the screenshot.

The file it's asking for have properly a diffrent number in ubuntu. Just check the installed files and make the symblink.

---

### Post by qrm on 2006-10-25
if Id only knew how to make a symlink

libgail versions : 0.8.11  and 1.9.3
libatk: 1.0-0

---

### Post by curvedinfinity on 2006-10-25
If thats a question, right click the file in nautilus (the file manager) and select "make link."

If you are trying to make a symlink for a file owned by root, open a terminal and run ...```
 sudo nautilus
``` .. and proceed as normal.

A symlink, by the way, is sort of like a shortcut in windows, except that Linux thinks the link is for all intents and purposes the actual file it links to as opposed to something like a hyperlink.

sure you can do it in a terminal, but its far more intuitive to do it in nautilus

---

### Post by Perfect Storm on 2006-10-25
```
sudo ln -s /usr/lib/libatk-1.0.so.0 /usr/lib/libatk-bridge.so
sudo ln -s /usr/lib/libgailutil.so.18 /usr/lib/libgail.so
```

This was done in edgy (so it might have another names in dapper), I have notice that there's way diffrent from what it ask for and what's available, so see this as an experiment.

If it fail you can delete the symblink
```
cd /usr/lib
sudo rm -rf libatk-bridge.so
sudo rm -rf libgail.so
```

---

### Post by qrm on 2006-10-25
well, im on edgy too an I was able to make the symlinks. But the racer installer still complains about those packges'

E: the errors arent the same ```
Gtk-WARNING **: Failed to load module "libgail.so": `gtk_module_init': /usr/lib/libgail.so: undefined symbol: gtk_module_init

Gtk-WARNING **: Failed to load module "libatk-bridge.so": `gtk_module_init': /usr/lib/libatk-bridge.so: undefined symbol: gtk_module_init
```

---

### Post by Perfect Storm on 2006-10-25
Do you have libgail-gnome-module installed?

---

### Post by qrm on 2006-10-25
```
ats@zanzhu:~$ sudo apt-get install libgail-gnome-module
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgail-gnome-module is already the newest version.

```

Ive had this problem since dapper, if it helps figuring out what the problem is

---

### Post by Perfect Storm on 2006-10-25
Hmmm...I'll take a look at it in the weekend and see if I can install it.

---

### Post by qrm on 2006-10-29
well, im having the exact same problem with warzone. Screenshot:
[[IMG]http://content.imagesocket.com/thumbs/warzone15f9.png[/IMG]](http://imagesocket.com/view/warzone15f9.png) 

well, symlinking didnt work and its still complaining about those libgail etc packages. Any help is greatly appreciated

---

### Post by qrm on 2006-10-30
bump

---

### Post by Perfect Storm on 2006-10-30
I just downloaded the beta version loki installer (english). It just install and run perfectly.
I've attached the torrent package:

Then unpack it and run the commands:
```
sudo sh racer_0.5.2beta8.9-english.run
```
When installed exit the installer and type **racer**. (don't hit the play button in the installer).

---

### Post by qrm on 2006-10-31
Ive been there and done that. I tried all the versions of racer I could get my hands on :) I kept trying installing racer and warzone and some moment they didnt open a ui but opened in terminal instead so I could isntall them - dint manage to make it reoccur. At the moment I tried playing warzone and it worked perfectly (just love this game, brings back the old times of RA). Havent tried racer yet but Ill let you know. If it helps solving the problem I should mention that this system has been upgraded through years from breezy to dapper and then edgy.

E: while warzone runs perfectly, trying to start racer from the added debian menu (the shortcuts dont show up on usual gnome applications - games menu) doesnt do anything. Trying to run it from the terminal I get :

```
/usr/local/bin/racer: 29: Syntax error: Bad substitution
```

E2: dont want to start another thread. How could I change the resolution in warzone? Or resize the window?

---

### Post by Perfect Storm on 2006-10-31
I think it's an upgrade (from dapper to edgy) that went wrong I guess. I made a clean install of edgy and havn't encountered any problems that people with a dist-upgrade have.

---

### Post by qrm on 2006-10-31
well I guess it must have gone wrong with upgrade from breezy to dapper (pre RC) because It didnt work in dapper either

Edit: the both games run (some probs with textures loading in racer) from the debian menu shortcuts.

---

### Post by qrm on 2006-11-06
well, just reinstalled edgy from scratch. First time running .run file I couldnt still select anything (those buttons) but it got installed, because the base install button was already active. I tried installing again and again the button for base install was not active and i couldnt select it :x

the error I get in the terminal is:
```
Gtk-WARNING **: Unable to locate loadable module in module_path: "libindustrial.so",

```

couldnt find anything alike in the synaptic either (all repos enabled)

---

### Post by Perfect Storm on 2006-11-07
First check if you have it in /usr/lib/gtk-2.0/2.10.0/engines

---

### Post by qrm on 2006-11-07
well, it seems so. 

```
ats@zanzhu:/usr/lib/gtk-2.0/2.10.0/engines$ dir
libclearlooks.so   libhcengine.so    libredmond95.so  libthinice.so
libcrux-engine.so  libindustrial.so  libsmooth.so     libubuntulooks.la
libglide.so        libmist.so        libsvg.so        libubuntulooks.so

```

I guess there needs some symlinking to be done, but where?

---

### Post by Perfect Storm on 2006-11-07
Which version of Ubuntu do you use? And is it 32bit/64bit or ppc? I'm asking because all the problem you ran into I've never experienced. It should work without any tweaking and hacking.

---

### Post by qrm on 2006-11-07
well im running the latest aka edgy 6.10 with generic kernel

E: its 32 bit and my processor is a p4 2,6 ghz with HyperThreading.

---

### Post by qrm on 2006-11-09
darn, I tried installing racer under the "real" terminal so that graphic librarys wouldnt affect me and I got it isntalled, the only thing is that I get this error when I try to run it from terminal:
```

/usr/bin/racer: 29: Syntax error: Bad substitution

```

even google didnt throw anything usable up :/

---

### Post by The J on 2006-11-11
To get rid of that "Bad substitution" error, I looked at the racer file (which is a script).  On line 29 is just a statement that appears to just print something to the terminal (echo).  I ended up deleting that statement and the "&&" before it on the previous line and that got it working.

---

### Post by qrm on 2006-11-14
thanks for the tip, ill try it t the very first possible moment :D

---

### Post by qrm on 2006-11-16
had to comment the whole section out with # -s (i dont like deleting code :D). Many thanks for the tip m8 :D

---

