---
title: "Dungeon Crawl Stone Soup, with tiles"
date: 2007-12-09
forum: Gaming &amp; Leisure
---

### Post by revolve on 2007-12-09
Does anyone know if there's an Ubuntu port of this wonderful, wonderful game? I've tried compiling but I cannot for the life of me understand the directions in the readme. Thanks in advance.

---

### Post by cogadh on 2007-12-09
There's really no such thing as an "Ubuntu port" of any software. Ubuntu is Linux, so anything that has a "Linux port" should work on Ubuntu. If you are having problems compiling and installing software from source, then this how-to might help some:
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

As for a precompiled Ubuntu package, the best place to look for one, if it isn't in the repositories, is at [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by awebster on 2009-05-24
hi,     I found this thread on google & wanted to share how I got stone soup with tiles to compile on ubuntu 9.04. ```
1. download the stone soup code from, [http://sourceforge.net/project/downloading.php?group_id=143991&filename=stone_soup-0.4.5-src.zip](http://sourceforge.net/project/downloading.php?group_id=143991&filename=stone_soup-0.4.5-src.zip).  Remember where it is!
2. install the following prerequisites before we compile
3. sudo apt-get install libpng3 
4. sudo apt-get install bison 
5. sudo apt-get install libpng12-dev
6. sudo apt-get install g++ 
7. sudo apt-get install libx11-dev 
8. sudo apt-get install flex 
9. navigate to the directory where you saved the stone_soup-0.4.5-src.zip file you downloaded in step #1. 
10. unzip stone_soup-0.4.5-src.zip 
11. cd stone_soup-0.4.5-src.zip 
12. cd source 
13. gedit makefile, at the start of the file change it from 
MAKEFILE ?= makefile.unix 
#MAKEFILE ?= makefile.dos 
#MAKEFILE ?= makefile.osx
#MAKEFILE ?= makefile.mgw 
#MAKEFILE ?= makefile_tiles.mgw 
#MAKEFILE ?= makefile.x11 
 to look like 
#MAKEFILE ?= makefile.unix 
#MAKEFILE ?= makefile.dos
#MAKEFILE ?= makefile.osx
#MAKEFILE ?= makefile.mgw 
#MAKEFILE ?= makefile_tiles.mgw
MAKEFILE ?= makefile.x11 
 and save the file.  

14. you should still be in the stone_soup-0.4.5-src/source directory.  Type make. 
 If everything compiles without error you can run stone soup with tiles by typing ./crawl!  
15. have fun!
```

---

### Post by del_diablo on 2009-05-24
Can anybody tell me why the people who write readme's tend to write it worse?

> 3. sudo apt-get install libpng3 
4. sudo apt-get install bison 
5. sudo apt-get install libpng12-dev
6. sudo apt-get install g++ 
7. sudo apt-get install libx11-dev 
8. sudo apt-get install flex 

Could have been:
> Please install following stuff from repo:
sudo apt-get install libpng3 bison libpng12-dev g++ libx11-dev flex

I would have done in asking people to rip it using svn of sourceforge, and made quite the mess that would have done the trick in 1 CnP(except makefiles that needs to be manually edited).

---

### Post by Lord_ on 2009-12-29
For version 0.5.2 (which is the only version I have tested)  i needed to also install 

sudo apt-get install libsdl-dev libsdl-image1.2-dev 

to get it to compiling with tiles.

---

### Post by djfraggle on 2010-01-27
Ok, so here's what I think should be some more concise instructions on compiling the newest version of DCSS with tiles as of this writing:

1. Download the stone soup code from, [http://sourceforge.net/projects/crawl-ref/files/Stone%20Soup/0.5.2/stone_soup-0.5.2-src.zip/download](http://sourceforge.net/projects/crawl-ref/files/Stone%20Soup/0.5.2/stone_soup-0.5.2-src.zip/download).  Remember where it is!
2. sudo apt-get install libpng3 bison libpng12-dev g++ libx11-dev flex libsdl-dev libsdl-image1.2-dev
3. navigate to the directory where you saved the stone_soup-0.5.2-src.zip file you downloaded in step #1. 
4. unzip stone_soup-0.5.2-src.zip 
5. cd stone_soup-0.5.2-src/source
6. gedit makefile (or your favorite text editor - mine is vim). At the start of the file change it from:
MAKEFILE ?= makefile.unix 
#MAKEFILE ?= makefile.dos 
#MAKEFILE ?= makefile.osx
#MAKEFILE ?= makefile.mgw 
#MAKEFILE ?= makefile_tiles.mgw 
#MAKEFILE ?= makefile.x11 
 to look like:
#MAKEFILE ?= makefile.unix 
#MAKEFILE ?= makefile.dos
#MAKEFILE ?= makefile.osx
#MAKEFILE ?= makefile.mgw 
#MAKEFILE ?= makefile_tiles.mgw
MAKEFILE ?= makefile.x11 
 and save the file.  

7. You should still be in the stone_soup-0.5.2-src/source directory.  Type make. If everything compiles without error you can run stone soup with tiles by typing ./crawl!  
8. Have fun!

Thanks to the previous posters for helping me get this compiled. I hope this helps others to get this great game going. FYI, I have tested this on 9.10 32 and 64-bit. Enjoy!

---

### Post by djfraggle on 2010-01-27
One more item of interest for those of you with dual monitor systems. To get rid of the extremely large window, uncomment the following lines in the tiles_options.txt file:

# tile_window_width = 1024
# tile_window_height = 768

Then change the dimensions to match your monitor's (unless you just want a 1024x768 window). Hope this helps.

---

### Post by moyergeo on 2010-02-27
Thanks everyone, and especially djfraggle - I'm new to Ubuntu and looking forward to some crawling. Unfortunately, following the steps I hit a snag and would appreciate if I can be told where I'm going wrong. My makefile looks like this:

MAKEFILE ?= makefile.unix
#MAKEFILE ?= makefile.dos
#MAKEFILE ?= makefile.osx
#MAKEFILE ?= makefile.mgw
#MAKEFILE ?= makefile_tiles.mgw
#MAKEFILE ?= makefile_tiles.unix

So there.s no makefile.x11 option... when I try to compile with another option selected there are errors. Anyhootles, not a big deal, but if you can help me I'd be very grateful.

---

### Post by moyergeo on 2010-03-05
Well there's a message that "Currently there are no pre-built packages for Linux distributions available." But why would that change in the same version number 0.5.2?

[http://crawl.develz.org/wordpress/downloads](http://crawl.develz.org/wordpress/downloads)

---

### Post by freeformschooler on 2010-03-05
If anyone wants, I could make a .deb of the 0.5.2 source, or the latest git. Got all the requirements, and checkinstall is awesome.

---

### Post by moyergeo on 2010-03-22
I'd love a .deb personally

---

### Post by freeformschooler on 2010-03-22
Well, 0.6.0 is EXTREMELY close to coming out as of a couple of days ago, so I'll probably wait 'till then. Sorry for the late reply.

---

### Post by moyergeo on 2010-03-22
> **freeformschooler said:**
> Well, 0.6.0 is EXTREMELY close to coming out as of a couple of days ago, so I'll probably wait 'till then. Sorry for the late reply.

You're not late, I think waiting for 0.6.0 is a good idea. Also I seem to be the only who hasn't been able to compile it on my own so please - don't rush on my account.

---

### Post by christhawkSMR on 2010-04-19
Any updates on putting this together?  No pressure - just curious & eagerly awaiting! :popcorn:

---

### Post by oldrocker99 on 2010-04-20
I followed the instructions, and got Error #2.

:confused:

:guitar:

---

### Post by eraevous on 2010-04-28
I too would love a package of the new SS tiles as well. You're awesome, thanks!

---

### Post by cascade9 on 2010-04-28
For some reason, I prefer it in ASCI, but I might have to try the tiled version again...maybe I'll like it more this time ;)

---

### Post by eraevous on 2010-04-30
If you're getting Error #2, it likely means that you're missing the dev version of some package or another. I was missing libsdl1.2-dev and libsdl-img1.2-dev. Look for "foo.h: No such file or directory"
messages where "foo" is something you're missing. Then try searching Synaptic for something like "libfoo" and install the package with "foo" and "dev"

---

### Post by kfazz on 2010-05-22
if anyone still needs binaries of crawl i've backported 0.6 from maverick to lucid. the debs for ascii and tiles (and the requisite -common package) are here [http://www.fileden.com/files/2010/3/21/2800273//crawl_0.6.0_lucid.zip](http://www.fileden.com/files/2010/3/21/2800273//crawl_0.6.0_lucid.zip)

---

### Post by lovecats on 2010-05-23
I also cannot understand the directions in the readme, Gosh


> **revolve said:**
> Does anyone know if there's an Ubuntu port of this wonderful, wonderful game? I've tried compiling but url=http://www.r4-ds-dsi.nl]r4i gold[/url] [r4  sdhc](http://www.r4-ds-r4i.fr) [r4i sdhc](http://r4-dsi.be) [r4  ds](http://www.r4isdhc.ch) [m3 ds real](http://www.r4dsi.at)  [acekard 2i](http://www.r4-dsi.de) [dstt](http://www.r4-dsi.it)  [dstti](http://www.r4-dsi.es)  I cannot for the life of me understand the directions in the readme. Thanks in advance.

---

### Post by formaldehyde_spoon on 2010-05-23
If you like Crawl, you can try Nethack (probably the most famous rouge-like [bar rogue of course!], the design of Crawl was based on it - it doesn't replace Nethack though, Nethack is continuously being actively developed). 

Nethack is in the repositories.

Crawl levels are more complex
Nethack item interaction is more complex. 
You will probably have to learn more in Nethack to win, and winning streaks are almost unheard of (although I read somewhere that Crawl is harder? Don't know...).   
Unknown items are more dangerous in Nethack.  
Vision in Stone Soup is symmetric (if you can see a monster he can see you), not so in Nethack.
Missile weapons in Nethack are fired in eight directions only.

---

### Post by cascade9 on 2010-05-26
> **formaldehyde_spoon said:**
> If you like Crawl, you can try Nethack (probably the most famous rouge-like [bar rogue of course!], the design of Crawl was based on it - it doesn't replace Nethack though, Nethack is continuously being actively developed). 

ADOM (ancient domains of mystery) is probably worth a look as well. 

Be warned, its a lot more complex than dungeon crawl or nethack.

---

### Post by NecroPsyChroNauTron on 2010-07-28
Thank you everyone!

---

### Post by Kwho on 2012-01-10
I can't figure out how to get make to work...

---

### Post by nothingspecial on 2012-01-10
This thread is old.

Please make a new one.

Closed.

---

