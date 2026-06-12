---
title: ".m4a support?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by SeanCallan on 2005-10-13
I'm using XMMS right now and I believe I have all the packages for it.

I from time to time get some problems where it thinks my card isn't connected, but then it'll work.

Anyways, is there anyway I can get it to support .m4a extensions or another other software that does?

---

### Post by kassetra on 2005-10-13
[quote=SeanCallan]I'm using XMMS right now and I believe I have all the packages for it.

I from time to time get some problems where it thinks my card isn't connected, but then it'll work.

Anyways, is there anyway I can get it to support .m4a extensions or another other software that does?[/quote]

If you're using XMMS - you'll need to install this plugin (the xmms one):
[http://fondriest.frederic.free.fr/realisations/](http://fondriest.frederic.free.fr/realisations/)

---

### Post by SeanCallan on 2005-10-17
Ok I went and downloaded everything.  But I'm having trouble installing it.

I'm reading the instructions and some of the commands it tells me to execute don't exists.   For example it tells me to just type "make" to compile the stuff; that doesn't work.

> 
sean@Doomspork:~/Desktop/xmms-mp4_20050213$ make
make: *** No targets specified and no makefile found.  Stop.
sean@Doomspork:~/Desktop/xmms-mp4_20050213$ ls
aclocal.m4      compile       config.sub    depcomp     Makefile.am  NEWS
AUTHORS         config.guess  configure     INSTALL     Makefile.in  README
autom4te.cache  config.h.in   configure.ac  install-sh  missing      src
ChangeLog       config.log    COPYING       ltmain.sh   mp4ff        TODO


edit:  I just realized when I run the configure file, it's failing to build the executables.  I have gcc installed but its failing.

> 
sean@Doomspork:~/Desktop/xmms-mp4_20050213$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


---

### Post by bionnaki on 2005-10-17
install build-essential, perhaps?

---

### Post by bionnaki on 2005-10-17
beep media player has a .m4a support plugin...beep & the plugin are available via synaptic - bmp is xmms, but better imho.

edit: sorry...I thought you said mp4....nevermind

---

### Post by SeanCallan on 2005-10-17
Well bmp is nicer looking then XMMS in my opinion, but are you saying it doesn't do m4a? :|

---

### Post by mostwanted on 2005-10-17
AFAIK Mp4 and M4a is the same thing (AAC files) they just use different file extensions.

Try installing the faad packages in synaptic, they decode aac files.

---

### Post by SeanCallan on 2005-10-17
I just tried to looking for the faad packages but I don't have them.  I have the universe enabled too.

I'll see if I can find them via google.

---

### Post by mostwanted on 2005-10-17
Hm... I have them, is multiverse enabled with you?  Or maybe they're in backports.

---

### Post by SeanCallan on 2005-10-17
I added the multiverse and found them.

I added bmp-mp4 and faad but I still can't play the .m4a extensions :|

---

### Post by Donza on 2005-10-18
It is same for me. I have installed bmp-mp4 and faad2 for beep-media-player but I can't play aac-audio :(. Has any of you got this combination or XMMS+mp4 working in breezy? You find aac streams for example [http://www.soma.fm]("http://www.soma.fm").

---

### Post by Donza on 2005-10-19
Okay. It seems that Rhythmbox plays aac-audio after I installed gstreamer plugins. But for some reason bmp and xmms are unable to play same files.

---

### Post by Donza on 2005-10-31
^up

Some help anyone?

---

### Post by mustang on 2005-11-02
I hate to revive a thread but I noticed Sean didn't solve his problem. 

I noticed that (atleast for me), XMMS does play m4a files while BMP didn't. This is because BMP doesn't have the proper plugins

Do this:

```
sudo cp /usr/lib/xmms/Input/libmp4.* /usr/lib/bmp/Input/
```

---

### Post by BurningToad on 2005-11-14
I just added "faad" and xmms-mp4 from the universe or multiverse or something, and opened up a .m4a file from file browser and it started working automatically in xmms.

---

### Post by BurningToad on 2005-11-14
However... it seems that sometimes at the end of a .m4a file, XMMS will totally mess up and thrash my hard drive, I can't seem to close it without resetting... 

Happened 3 times now

---

### Post by sciurus on 2005-12-25
For Rhythmbox install gstreamer0.8-faad. For Beep Media Player (ie- GTK2 XMMS) install bmp-mp4. For XMMS install xmms-mp4. If you use both XMMS and BMP, it might be possible to only install the plugin for one and create a link to it in the other program's plugin directory.

---

### Post by skralljt on 2007-07-03
I've installed xmms-mp4, libfaad2-0, and yet xmms 1.2.10  is unable to add an m4a file.  xfmedia plays them just fine hough!  How very strange, I just want to use xmms so that I can get more details about my cd rip than other rograms provide.

---

