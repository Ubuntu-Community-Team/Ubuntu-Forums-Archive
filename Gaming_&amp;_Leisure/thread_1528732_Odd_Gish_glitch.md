---
title: "Odd Gish glitch"
date: 2010-07-11
forum: Gaming &amp; Leisure
---

### Post by pieman711 on 2010-07-11
I've got the humble bunch and managed to install them with out any  problems (except Lugaru, clicking on the .bin file did nothing and I had  to run it from a terminal) I've recently started playing Gish and have  noticed some odd behaviour depending on how I open the file. 
I have it saved on a seperate partition from my linux install because  I'm trying to keep all of my games together and somewhere where I have a  lot more space. It's saved to /media/D/Games/gish153 and I've edited  fdisk to make sure D is mounted automatically when I boot my computer 

If I double click on the icon in nautilus it runs completely fine, the  problem is when I try and use the command line, run applications or the  menu item.
By running it like this in a terminal....

```
pieman@pieman-desktop:/$ /media/D/Games/gish153/./gish
AL lib: ALc.c:1420: alcDestroyContext(): deleting 13 Source(s)
AL lib: ALc.c:1818: alcCloseDevice(): deleting 32 Buffer(s)
pieman@pieman-desktop:/$ 

```It loads up a grey window with no graphics at all and the only option is to close it using teh cross at the top. 

if I cd to the gish directory first...

```
pieman@pieman-desktop:/$ cd /media/D/Games/gish153/
pieman@pieman-desktop:/media/D/Games/gish153$ ./gish
AL lib: ALc.c:1420: alcDestroyContext(): deleting 13 Source(s)
AL lib: ALc.c:1818: alcCloseDevice(): deleting 32 Buffer(s)
pieman@pieman-desktop:/media/D/Games/gish153$
```then it runs fine again!
unfortunatly in my menu>applications>games I can't find a way of getting it to cd before trying to run ./gish so it just brings up the broken window.

I also want to put that games directory in to my $path and get it to automatically include any folders put into that directory, is that possible? I don't want to have to edit my bash.rc file ever time I install a new game

Thanks for your help

---

### Post by DrMelon on 2010-07-11
The reason why it runs oddly if you just run from the terminal without changing directory (and you type in the full directory) is becaus Gish looks for its files in the current directory - so it will be looking in the wrong place if you haven't changed directory first. Quite a few Linux games are known to do this.

---

### Post by pieman711 on 2010-07-11
I see, that makes sense. So even though I told it where to look for the program to run it was still looking in the home folder for the included files. 
So what can I put in my menu to make it run properly? And any idea on how to get my $path to automatically include all the folders in a particular directory? although I suppose I will have exactly the same problem even if it is in $path (ie just typing "gish" into a terminal)

---

### Post by pieman711 on 2010-07-12
After some more searching on google I've managed to find a workaround for getting gish to run from a launcher in menu. I'll post it here incase anyone else has a similar problem...

[http://www.pontifex2.com/smf/index.php?topic=987.0](http://www.pontifex2.com/smf/index.php?topic=987.0)

---

