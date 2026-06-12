---
title: "Rhythmbox 0.12.2 install error on Intrepid"
date: 2009-05-31
forum: General Help
---

### Post by brookie on 2009-05-31
Hello,

I was wondering if anyone else has successfully installed Rhythmbox 0.12.2 on intrepid. 

It was just updated and can be found here: [http://projects.gnome.org/rhythmbox/]("http://projects.gnome.org/rhythmbox/")

The output from my ./configure is: 
checking for RB_CLIENT... configure: error: Package requirements (glib-2.0 >= 2.16.0 gio-2.0 >= 2.16.0) were not met:

No package 'glib-2.0' found
No package 'gio-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables RB_CLIENT_CFLAGS
and RB_CLIENT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
....................

I checked Synaptic Package Manager for the glib-2.0 and gio-2.0 so install them but they are not listed in Synaptic. 

I just thought it would be fun to install the latest version of Rhythmbox since it has some bug fixes in it. 

Any help would be greatly appreciated. 
Cheers,
Brookie

---

### Post by fillintheblanks on 2009-05-31
I havent had much luck getting the new rhythmbox to work but you did type

**sudo apt-get build-dep rhythmbox** right?

---

### Post by brookie on 2009-05-31
hi,
no i actually untarred the file, cd'd to the directory and typed ./configure in the terminal as stated in the INSTALL file. i'll give it a shot though and let you know if it worked. 

the command won't work on the file i downloaded from gnome
here's the output:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for rhythmbox

i've tried it on the untarred directory, on the compressed file

---

### Post by brookie on 2009-05-31
okay, i tried sudo apt-get build-dep rhythmbox on the source file from: 
[http://gnomefiles.org/app.php/Rhythmbox]("http://gnomefiles.org/app.php/Rhythmbox")

it ran a lot of stuff (8min) but i cannot find a deb file for rhythmbox anywhere 

afterwards i ran ./configure again ...and i get the following error

configure: error: totem playlist parsing library not found or too old

it's a totally different error now.
hmmm...??? any ideas?

---

### Post by brookie on 2009-05-31
bump?
anyone know what this configure error is?

checking for TOTEM_PLPARSER... no
configure: error: totem playlist parsing library not found or too old

synaptic shows libtotem-plparser12, and libtotem-plparser-dev are installed

i can't find a dependency list on the gnome rhythmbox site

---

### Post by Yellow Pasque on 2009-05-31
The version of libtotem-plparser included with intrepid (2.24.2) is probably too old. AFAICT, Rhythmbox 12.x requires at least 2.24.3

---

### Post by brookie on 2009-06-01
Thanks Temujin,
I searched for packages at Ubuntu and found a newer version of it there. 

[http://packages.ubuntu.com/jaunty/libtotem-plparser-dev]("http://packages.ubuntu.com/jaunty/libtotem-plparser-dev")

After work I'll try to install it with it's dependencies. Hope I can get it to work without screwing up my Intrepid install too much. 

The libtotem-plparser was updated to libtotem-plparser-dev (2.26.1-0ubuntu1) in jaunty and libtotem-plparser-dev (2.27.1-0ubuntu1) in karmic.

Should I try the jaunty package. I would just use jaunty but my upgrade did not go well, with no use of usb mouse or keybpard so I just upgraded my hard drive and stuck with intrepid.

Any suggestions before I continue? Thanks. :)

---

### Post by Vadi on 2009-06-02
[http://www.getdeb.net/app/Rhythmbox](http://www.getdeb.net/app/Rhythmbox)

---

### Post by brookie on 2009-06-02
I tried that too. The deb install failed because it does not meet one of the dependencies. I looked on the ubuntu website where there packages are. If you upgrade one package, then it has dependencies for other packages, and blah, blah, blah. 

Basically the Gnome/Rhythmbox music player is architecture dependent. In other words, if you are not running the latest and greatest version of Ubuntu, you'll be stuck with the old Rhythmbox version with bugs included. 

I'm thinking about going to Banshee or another player that isn't architecture dependent. It was fun trying to upgrade though.

---

