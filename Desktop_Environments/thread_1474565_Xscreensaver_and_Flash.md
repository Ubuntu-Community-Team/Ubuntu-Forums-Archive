---
title: "Xscreensaver and Flash"
date: 2010-05-06
forum: Desktop Environments
---

### Post by MidnightSon on 2010-05-06
Hi guys,

First of all, I'm new at Linux (really started yesterday), and french, so sorry for the mistakes I may make.
I'm working right now (during my period of work experience) at getting a flash screensaver (developed on Win & Mac) to run on Ubuntu.
I gathered quite a lot of stuff from different forums (including this one) and sites, but none was satisfactory and I still have difficulties in understanding how the whole thing works.

Basically, I deactivated gnome-screensaver and installed xscreensaver instead.
I now have to configure it to launch a .swf file (or more precisely a whole folder full of .swf and .xml files, but we'll see later) as a scrensaver.
I found this [here]("http://www.jwz.org/xscreensaver/faq.html#mpeg") :
> Macromedia's     [     stand-alone Flash player]("http://www.macromedia.com/support/flash/downloads.html") has xscreensaver support, as of      version 6.0.79 and later.  To use it, put a line like this in the     `programs' preference in your .xscreensaver file:        
[LIST]
[*]```
"My Flash"   gflashplayer -root $HOME/movies/my_flash.swf  \n\
```
[/LIST]
And did it (of course changing the path to mine), adding it at the first line of the document.
But what now ?

I also read something about using gflashplayer with xscreensaver, but I don't know how.
Plus, gflashplayer gives me this error when I try to open a .swf directly :
> An error occurred
GStreamer encountered a general supporting library error.I don't know if you guys know another way to do that.
Maybe I'll have to write a small program to launch the screensaver separately. I don't know. And I wouldn't know how to do that.

Any help is welcome, even tiny. I'm ready to spend quite some time energy on this one.
Thanks a lot for helping.

---

### Post by rCXer on 2010-05-06
Open the terminal and run...
```

xscreensaver-demo

```

On the "Display Modes" tab, is "My Flash" one of the screensavers listed?

---

### Post by MidnightSon on 2010-05-07
Hi there,

Thank you for your answer.

Yes, "My Flash" is listed.
I have created two entries in .xscreensaver :
```
"My Flash"     gnash $HOME/movies/myflash.swf -root      \n\
"My Flash 2"     gflashplayer $HOME/movies/myflash.swf -root      \n\
```
In the "Display Modes" list, "My Flash" is written in black (=installed) but the preview just loads a black screen.
When I right-click on the file myflash.swf and choose "open with gnash swf viewer" it does load normally in gnash, which means it's installed and working fine.

Also, "My Flash 2" is written in grey (=not installed) and that's why I tried with gnash instead of gflashplayer. I get this error when trying to load the preview :
> exec: 1: gflashplayer: not found
xscreensaver: 10:25:15 0: child pid 3582 (gflashplayer) exited abnormally (code 2)
Where "10:25:15" and "3582" increase each time I try to load it. The first line certainly means gflashplayer is not installed. I tried but didn't manage to find it anywhere (except online on [http://gflashplayer.klik.atekon.de/](http://gflashplayer.klik.atekon.de/) but even after installing klik and the libs - some of which are still missing - it won't load and I get an error from klik). I don't know what the second line means.

Do you understand better than I do ? What would you suggest ?
Thanks again for your help =)

---

### Post by MidnightSon on 2010-05-11
Bumping that.

---

### Post by rCXer on 2010-05-12
I have no idea what to do next.  Maybe you should start a new topic asking how to install gflashplayer.  Good Luck :)

---

### Post by MidnightSon on 2010-05-12
Ok. Thanks anyway =)

---

