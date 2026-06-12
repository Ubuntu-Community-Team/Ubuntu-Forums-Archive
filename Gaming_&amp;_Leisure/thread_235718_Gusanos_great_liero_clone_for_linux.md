---
title: "Gusanos: great liero clone for linux"
date: 2006-08-13
forum: Gaming &amp; Leisure
---

### Post by NickeM on 2006-08-13
I found this great game was mentioned over at [freegamer blog]("http://freegamer.blogspot.com/") and i managed to get it to work with Ubuntu Dapper

Charles Goodwin author of freegamer posted my letter which have some clues how to get Gusanos to compile and run.

I have made a deb if there is anyone interested in trying this game out, be warned that it includes both fmod(audio) and zoidcom(networking) libraries which are closed sourced. Both libraries are free to distribute for non-commercial purposes.

Gusanos running under Ubuntu dapper:
[darkmod picture]("http://ubuntuforums.org/gallery/showphoto.php?photo=3285&cat=500")
[doom mod]("http://ubuntuforums.org/gallery/showphoto.php?photo=3286&cat=500")

Download Gusanos 0.9c(deb) from rapidshare.de:
[http://rapidshare.de/files/29278331/gusanos09c.deb.html](http://rapidshare.de/files/29278331/gusanos09c.deb.html)

Instructions for playing the game, the game menu doesn't have user options yet so you have to modify the /opt/gusanos/default/config.cfg

I have mapped these keys:
fire           - left control
change weapons - alt
jump           - space
Movement       - arrow keys
F1             - opens console

console commands:
say <message>
addbot <name>
game  <name>  - change to a different mod, default mod is <default> suprise  :mrgreen: 

There are a couple of issues of Power Magazine (liero/gusanos fanzine) included in the gusanos09c.deb which can be found under /opt/gusanos/pdf.

I am not certain that the desktop file i provided under /usr/share/applications will work for everyone, but the game can always be started from the terminal, just type gusanos and press enter.

Happy gaming!
/Nicklas

---

### Post by amsoml on 2006-08-15
regarding fmod, I've made a patch to use OpenAL (open source) instead. Looks like it will not integrate into the main code as the   next version is supposed to be a complete rewrite in a different dev lang.
I might look into the bots AI once I have the time.

happy gaming!
btw:why doesn't anyone play a different mod than default?

---

### Post by NickeM on 2006-08-16
Yes!, i have been wondering that too..since there are a lot of great mods for gusanos, it think doom mod and the dark mods looks great. I saw that gliptic had made a bugfix for 0.9d regarding playing mods.

Good to hear that fmod is replaced, i saw something on the gusanos forums that they are going to replace zoidcom with their own network library.

---

### Post by NickeM on 2006-08-25
Setrodox has kindly offered to host the gusanos deb packages on his server: [Here]("http://www.powerhuhn.net/depot/gusanos/gusanos/gusanos09c_xxl.deb") No more "sucky" rapidshare ;-) Happy gaming!

Gusanos has got an entry at The Linux Game Tome, [Link]("http://www.happypenguin.org/show?Gusanos")

---

### Post by Iandefor on 2006-09-04
Excellent! The only thing I've been missing since going Windows-free was a decent Liero clone. Thanks for the tip!

---

### Post by patsissons on 2007-03-31
Does anyone still have the gusanos deb kicking around?  building this game is like trying to build an igloo on the sun.  I have given up and would like to just install the binaries.  only problem is that the server where it used to be hosted is no longer responding.

---

### Post by PhatStreet on 2007-03-31
[http://www.mediafire.com/?7dwwwmo5yyd](http://www.mediafire.com/?7dwwwmo5yyd)
This includes a bunch of mods. Doom is especially fun to play. 

Fortunately for those who can't compile (I never could either), Gusanos 1.0 will be a total rewrite and will likely use SDL and OpenAL rather than Allegro and Fmod. The networking library Zoidcom is still an issue, though, as basara hasn't found a replacement he likes.

---

### Post by vanadan on 2008-03-29
seems quite impossible to get the deb.. 

is it possible to compile and run it on gutsy?

tried something and got this:

merlin@bedna:~/gusanos/Console$ make
g++ -c console.cpp -O3 -mwindows 
cc1plus: error: unrecognized command line option "-mwindows"
make: *** [console.o] Error 1

any idea why, or what i did wrong..?

---

### Post by vanadan on 2008-04-03
another try ended like this:

engine.cpp:70: error: cannot allocate an object of abstract type ‘Client’
network.h:40: note:   because the following virtual functions are pure within ‘Client’:
/usr/local/include/zoidcom/zoidcom_control.h:558: note:         virtual void ZCom_Control::ZCom_cbConnectionClosed(ZCom_ConnID, eZCom_CloseReason, ZCom_BitStream&)
/usr/local/include/zoidcom/zoidcom_control.h:605: note:         virtual void ZCom_Control::ZCom_cbNodeRequest_Dynamic(ZCom_ConnID, ZCom_ClassID, ZCom_BitStream*, eZCom_NodeRole, ZCom_NodeID)
/usr/local/include/zoidcom/zoidcom_control.h:621: note:         virtual void ZCom_Control::ZCom_cbNodeRequest_Tag(ZCom_ConnID, ZCom_ClassID, ZCom_BitStream*, eZCom_NodeRole, zU32)
make: *** [engine.o] Error 1
merlin@bedna:~/sys/gusanos/zoid$ 

pity.. it seemed like one of the most similar to the original - therefore nicest - liero clones from the screenshots..

kinda hoped there would be the original liero sounds, i havent heard them for ages.. not since my first computer rousted its cpu.. :/

---

### Post by Feliz Lombriz on 2009-06-28
There is a new package of Gusanos out there that is supposed to be relatively easy to compile on Linux. A Linux-savvy pal and I tried to compile it without any success, but it could work for others. The game is a blast if you can get it up and running with some good mods, so give it a try. (And if you figure out what we were doing wrong before don't be shy. ;) I'd like to get a smoothly compilable package to put up on GusanosFiles.)

[GusanosFiles - Download Page]("http://sites.google.com/a/gusanosfiles.co.cc/home/programs")
--Download "Gusanos 0.9c Linux Pack" (The mirrored version at Pordesign.eu is the recommended version of the download)

Good luck and have fun!

-Feliz

---

### Post by nukenk on 2009-07-21
Here's the deb for gusanos09c that I came across in google search

[http://gusanos.ragzouken.com/gusanos09c.deb](http://gusanos.ragzouken.com/gusanos09c.deb)

But could not get it to install. Please drop a line if you are able to.Thanks

---

