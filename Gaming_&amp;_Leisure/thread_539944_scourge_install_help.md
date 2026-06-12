---
title: "scourge install help"
date: 2007-08-31
forum: Gaming &amp; Leisure
---

### Post by motorman on 2007-08-31
ok ive tried to install s.c.o.u.r.g.e.  and i can only get so far before i cant do anything else what am i doing wrong i have run   "sudo apt-get install libfreetype6 libgl1-mesa libglu1-mesa libsdl1.2debian libsdl-mixer1.2 libxmu6" 
and i still get stuck this is the install instructions im using

# To configure it
cd scourge/scourge
autoreconf -i

# To compile it
cd ..
mkdir build
cd build
../scourge/configure --enable-debug
make

# Run
./src/scourge -f     

and iv got to where the prompt says : scourge/scourge build$  any help will be welcome thanks

---

### Post by Perfect Storm on 2007-09-01
If you're new to linux/ubuntu world you should avoid compiling - here's a .deb of it: [http://www.getdeb.net/search.php?keywords=scourge](http://www.getdeb.net/search.php?keywords=scourge)


By the way you need the -dev libs for compiling the sources.

---

### Post by cahumphrey on 2007-09-05
thanks for this link, it worked perfectly for me!

---

### Post by plinydogg on 2009-01-01
Does anyone have a working link to the latest .deb installer? Thanks!

---

### Post by blackmoons on 2009-01-01
well, the list is getting long, isn't it, and I haven't even covered the half of it with thoughtful bloggers (not just photobloggers) out there who have managed to make me see and think in different ways, as well as the hundreds of talented photographers and other visual artists who continue to serve as inspiration.  It was tough keeping up with all the photoblogs, though I did what I could with visits to the ones I listed on my sidebar. Probably my favorite photoblog apart from John's was Gayla's making happy, which I never get tired of visiting.  Both John and Gayla use multiple cameras to explore, to engage in inquiry, to have fun with old quirky cameras, to just enjoy the process of taking pictures.  There's a lot to be said for that.

---

### Post by jrogers360 on 2009-01-02
Try these:

[http://ftp.akl.lt/Linux/Ubuntu/getdeb/sc/scourge-data_0.18-1~getdeb1_all.deb](http://ftp.akl.lt/Linux/Ubuntu/getdeb/sc/scourge-data_0.18-1~getdeb1_all.deb)
[http://ftp.akl.lt/Linux/Ubuntu/getdeb/sc/scourge_0.18-1~getdeb1_i386.deb](http://ftp.akl.lt/Linux/Ubuntu/getdeb/sc/scourge_0.18-1~getdeb1_i386.deb)

or 64bit:
[http://ftp.akl.lt/Linux/Ubuntu/getdeb/sc/scourge_0.18-1~getdeb1_amd64.deb](http://ftp.akl.lt/Linux/Ubuntu/getdeb/sc/scourge_0.18-1~getdeb1_amd64.deb)

---

### Post by Fenris_rising on 2009-01-09
Hi all
I to am having trouble with scourge. I have spent 3 days trying to install it. I have tried from the source and data files also the deb file. I have managed to satisfy the dependancies but when I try to run the game after compiling and install it throws the error up that the DATA is missing. Is there a concise guide to installing scourge. I have 8.04.1 on an eee pc. I fully suspect I am lacking in certain understandings of installing this particular item so be gentle with me :D

Forget it 2 minutes after posting I found the solution.........i've only been looking for 3 days! Works fine on an 904hd eee pc


regards

---

### Post by Mayfairy on 2009-03-15
Same here. The compiling stops at ./configure with the message "Cannot find SDL_ttf library" and I've tried many times, also downloaded the source from several different places. 

The .debs up there have a "scourge-data" dependency not satisfied.

EDIT: 

Installing cl_sdl_ttf through Synaptic got me a bit more forward. 
Installing it wanted to install cl_sdl as a dependency.

EDIT: 

Yep, that solved it. Managed to make the game work. 

Btw, that cl_sdl_ttf wasn't mentioned anywhere as a requirement for the game. Might be useful for adding it if developers of the game stop by here. This is with Ubuntu 8.04

---

