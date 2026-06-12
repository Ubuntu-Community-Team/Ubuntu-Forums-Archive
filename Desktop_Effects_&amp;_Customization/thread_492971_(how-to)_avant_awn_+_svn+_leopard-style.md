---
title: "(how-to) avant awn + svn+ leopard-style"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by ykpaiha on 2007-07-05
I loved it so much that I wanted to share it with you .
Unfortunatly checkinstall made odd things on my system...
so what is the point 
Make AWN look like leopard-osx-bar

Warning remove any awn preinstalled !!!

1) create a svn dir 
mkdir ~/svn
cd svn

2) download awn -svn
svn checkout [http://avant-window-navigator.googlecode.com/svn/trunk/avant-window-navigator](http://avant-window-navigator.googlecode.com/svn/trunk/avant-window-navigator)
it will ceate a dir in svn and download awn-svn

3)download The patch
[http://pastebin.ubuntu-nl.org/28405/plain/](http://pastebin.ubuntu-nl.org/28405/plain/)
save the file as patch.diff
copy this file into your  avant-window-navigator new created directory

4) apply the patch
cd ~/svn/avant-window-navigator
sudo patch -p1 < patch.diff
wait wile the patch is applied

5)run the compile
 ./autogen.sh --prefix=/usr
NB: do not forget the dot at the beginning and --prefix will mean that it will be compiled in usr/bin, the standard way is usr/local/bin , if so do not use the prefix
make
sudo make install

6)now you can go ahead
usr/bin/avant-window-navigator
or 
usr/local/bin/avant-window-navigator
if you didn't use the prefix
and fill up your dock

If tou want to load it automaticly
system=>preferences=>session 
and add an entry to be loaded on startup

7) now the WOW !..vista way sorry OSX way
gconf-editor
apps=>avant-window-navigator=>bar
bar angle change the value (right clic and edit) by 30
icon offset = 15 (same way)
it will give you the same look as the image here.
fell free to change it your way and post your results


8) enjoy and let me know if this is usefull to you.

---

### Post by 71CH on 2007-07-05
are you supposed to change the corner radius in gconf-editor?
i don't see an option for bar angle

---

### Post by ykpaiha on 2007-07-05
I just put a capture of my gconf I didn't changed anything else than the 2 cited variable.
I will chang some other to see or let me know.
I changed as well the bar height value to 56 to have lager icons dock
the forum for awn and the basis of this post is here;
[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=319&page=1](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=319&page=1)

---

### Post by detroit/zero on 2007-07-05
I just installed AWN through Synaptic, and I'd like to apply that patch but I'm not sure what to do with it. Help, please? Also, I'm trying to figure out a way to stick the systems Main Menu (not the menu bar, but the Main Menu with just the Ubuntu icon..) and the Notification Area into the AWN bar. Any ideas? It'd be a heckuva lot easier if right-clicking could give an Add to Panel dialog like regular Gnome panels, but it doesn't.. and I'm not yet one with the Gnome panels.

Thanks for any help..

---

### Post by ykpaiha on 2007-07-06
> **detroit/zero said:**
> I just installed AWN through Synaptic, and I'd like to apply that patch but I'm not sure what to do with it. Help, please? Also, I'm trying to figure out a way to stick the systems Main Menu (not the menu bar, but the Main Menu with just the Ubuntu icon..) and the Notification Area into the AWN bar. Any ideas? It'd be a heckuva lot easier if right-clicking could give an Add to Panel dialog like regular Gnome panels, but it doesn't.. and I'm not yet one with the Gnome panels.

Thanks for any help..

to apply a patch you may apply it before to compile.
I guess sometime this will be included in a deb but actually i prefer not to provide it as it mess my system
Just the make install worked.
for the menu I have no clue if it's possible, but perso Idon't see the point to do so.
in the compile you have 2  avalaible applets : trash and workspace-switcher.

---

### Post by chaser209 on 2007-07-06
Please help:

I get all the way through everything, but when i get to the steps where i do "make" and "make install" i get the messages

"***No target specified and no make file found. Stop"

what am I doing wrong?

i also get a message after doing autogen that says something about makefile.in.in being out of date and using --force to overwrite.

---

### Post by Seine on 2007-07-06
If we install by hand with this patch, this means the package wont automatically be upgraded anymore, right?

Given that it seemed to easy to patch, will it be long before leopard-style awn makes it into the upgrades?

---

### Post by xfile087 on 2007-07-08
Thanks for the how-to - looks pretty slick on my machine!!!

Shame the trash applet doesn't work properly though....

---

### Post by isaacj87 on 2007-07-08
so I finally got this all installed and it does look pretty great...but it start to use up memory fast...how would one go about removing this?? I didn't use the "--prefix" is there a uninstall script?

BTW: I just checked it's usage and everytime I run my mouse over AWN or click a launcher it eats, and i mean eats memory...I got it up to 60 mb...that's getting out of hand

EDIT: Sorry, I just realized that "sudo make uninstall" works. Even better news though, there's a patch I found on a forum that seems to have fixed the memory leak issues. I can put it up here if someone wants it.

---

### Post by jputman01 on 2007-07-08
ok, i have followed these steps 3 times now and when i go to gconf-settings i dont have an option for icon offset

everything else is fine but i cant offset the icons, can anyone help!!

---

### Post by jputman01 on 2007-07-09
> **jputman01 said:**
> ok, i have followed these steps 3 times now and when i go to gconf-settings i dont have an option for icon offset

everything else is fine but i cant offset the icons, can anyone help!!

ok i got this fixed, i needed to make the patch executable

now another issue, why dont the icons on my dock move. on my old version the icons would move as i moved my mouse over them. now they just stay stationary, any ideas?

---

### Post by bimmerd00d on 2007-07-09
what are the odds this could be included in the repo version?

---

### Post by andrewsomething on 2007-07-09
> **bimmerd00d said:**
> what are the odds this could be included in the repo version?

I'm sure that it will eventually make it to the repo, but it's still a bit unstable. Judging by the pace people are contributing at over on the AWN forum, it shouldn't take very long.

For now, the is a deb availiable for download at: [http://download.tuxfamily.org/syzygy42/static/misc/packages/awn214reflect/](http://download.tuxfamily.org/syzygy42/static/misc/packages/awn214reflect/)

Just remember, this is still considered unstable. Also, you'll have to uninstall the repo version first which means no more automatic updates.

---

### Post by Iscin on 2007-07-18
Worked a treat, thanks mate :D.

---

### Post by SkiesOfAzel on 2007-07-18
The patch is already included in the latest svn, you don't need to apply it anymore.

---

### Post by slughappy1 on 2007-07-19
So I was able to mkdir svn, but when I tried to do the second step I got this error.

jason@jason-laptop:~/svn$ svn checkout [http://avant-window-navigator.google...ndow-navigator](http://avant-window-navigator.google...ndow-navigator)
svn: PROPFIND request failed on '/'
svn: PROPFIND of '/': Could not resolve hostname `avant-window-navigator.google...ndow-navigator': No address associated with hostname ([http://avant-window-navigator.google...ndow-navigator](http://avant-window-navigator.google...ndow-navigator))
jason@jason-laptop:~/svn$

---

### Post by djrobthaman on 2007-07-20
> **SkiesOfAzel said:**
> The patch is already included in the latest svn, you don't need to apply it anymore.

I have the svn from the [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) repo for awn.  Are you using another repo?

---

### Post by misfitpierce on 2007-07-20
I got it... looks great

---

