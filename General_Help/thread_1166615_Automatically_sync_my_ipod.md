---
title: "Automatically sync my ipod?"
date: 2009-05-21
forum: General Help
---

### Post by AllRadioisDead on 2009-05-21
Is there a program available that can automatically sync my ipod with a given directory? I don't want a big fancy media player that plays everything under the sun and manages my devices, so I'm thinking of using a terminal based music player, but I still need something to sync my ipod when my collection is updated, does anyone have anything that will do the trick?

---

### Post by Chemical Imbalance on 2009-05-21
Check out gtkpod.

It has this option, though I choose to manually sync my files.

---

### Post by Jazzy_Jeff on 2009-05-21
I also use gtkpod. Nice and simple.

---

### Post by AllRadioisDead on 2009-05-21
Anything "lighter"? I'm trying to go really minimalistic, this will do though if there's nothing better. Thanks guys!

---

### Post by Chemical Imbalance on 2009-05-21
Lighter?  For a GUI app, it doesn't get much lighter.

You must want a CLI app? 

I don't have any recommendations for any with iPod.

---

### Post by AllRadioisDead on 2009-05-21
Thanks for the reply. I was looking through the repos, and I found a package of interest called "gnupod". I did a bit of searching and I found this article:
> **Gnupod tools - terminals don&#8217;t bite**

 If you hate the graphical user interface or simply prefer to work with fast console tools, the utilities from **gnupod-tools** package may be useful to you. Some essential scripts are presented below.
 
[LIST]
[*] **gnupod_addsong** - can be used to add new songs to the iPod database. We can add a song to one or many playlists, modify ID3 tags (which are used for song metadata organizing), and even modify the quality (and the size) of a song while copying it to our iPod (option --reencode=int, where int=0..9 - the higher value, the worse quality and smaller size).
[*]**gnupod_check** - together with --fixit option checks and repairs potential problems with iTunesDB (the problems can be caused if you unplug iPod without unmounting it, as well as by some bugs in the software used to manage your iPod)
[*]**gnupod_search** - a command which helps to search through iPod library as well as modify the ID3 tags of selected songs on the fly. What is not so intuitive, the command can be also used for removing tracks from an iPod.
[/LIST]

Is this what I'm looking for? 
Source: [http://polishlinux.org/apps/ipod-in-linux/](http://polishlinux.org/apps/ipod-in-linux/)

---

### Post by Chemical Imbalance on 2009-05-21
> **ihermit said:**
> Thanks for the reply. I was looking through the repos, and I found a package of interest called "gnupod". I did a bit of searching and I found this article:

Is this what I'm looking for? 
Source: [http://polishlinux.org/apps/ipod-in-linux/](http://polishlinux.org/apps/ipod-in-linux/)

Don't know if that automatically syncs.

Try it and read the man page I guess.

---

### Post by AllRadioisDead on 2009-05-21
> **Chemical Imbalance said:**
> Don't know if that automatically syncs.

Try it and read the man page I guess.
It looks to me that it's just a collection of terminal scripts.
Surely a script could be created, if my ipod is connected, sync with my music folder?
To be honest, I don't mind if that's not possible, but syncing via a terminal command would be sweet.

---

### Post by cdude on 2009-05-22
> **Chemical Imbalance said:**
> Lighter?  For a GUI app, it doesn't get much lighter.

You must want a CLI app? 

I don't have any recommendations for any with iPod.

Actually there is a lighter gui app, [_Hipo_]("http://projects.gnome.org/hipo/"); a mono based app. it is very nice but I do not know if it is still in development (maybe the svn branch).

There are two other apps (perhaps not as light as hipo), [_Floola_]("http://www.floola.com/modules/wiwimod/") and [_YamiPod_]("http://www.yamipod.com/main/modules/home/"); they are not Linux specific, but I believe they'll do the job. I think they are free but not open source.    

Myself, I use banshee for music playing and ipod synchining.

A good source for gtk apps (and some others) go to [_gnomefiles.com_]("http://www.gnomefiles.org/index.php")

---

