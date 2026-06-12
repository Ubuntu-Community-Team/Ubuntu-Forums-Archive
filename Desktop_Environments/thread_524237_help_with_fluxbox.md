---
title: "help with fluxbox"
date: 2007-08-12
forum: Desktop Environments
---

### Post by kike_coello on 2007-08-12
hello all, is there a way to modify the menus on fluxbox when you click on the desktop?

also for blackbox, i only get "xterm, restart and exit" on the menu and i would like to add more stuff, like different apps

so far i've written a script that starts up beep media player, xfmedia and background but i would like this stuff to be available from the mouse,

also, what about icons? there aren't any, how can i add them?

please help, i use an old celeron 700mhz and gnome runs slow on this computer. 

thanks

---

### Post by kerry_s on 2007-08-12
click on xterm
type> sudo update-menus

sudo apt-get install rox-filer

use> rox -p=icons

don't forget to add it to your ~/fluxbox/startup

rox -p=icons &

---

### Post by K.Mandla on 2007-08-12
There's also a utility called [iDesk]("http://packages.ubuntu.com/feisty/x11/idesk") that gives you good control over desktop icons, if you aren't keen on using rox-filer. iDesk is in the repos, and there's a simple configuration tool called [idesktool]("http://www.jmurray.id.au/ideskconf.html") that you can use to set them up (it's easier than editing the text files).

---

### Post by kerry_s on 2007-08-12
> **K.Mandla said:**
> There's also a utility called [iDesk]("http://packages.ubuntu.com/feisty/x11/idesk") that gives you good control over desktop icons, if you aren't keen on using rox-filer. iDesk is in the repos, and there's a simple configuration tool called [idesktool]("http://www.jmurray.id.au/ideskconf.html") that you can use to set them up (it's easier than editing the text files).

hey, i wished i knew about idesktool sooner. i just used idesk for a friends desktop a couple of days ago and setting up the icons was really time consuming. :) the easy part was setting up the rotating background. it gave his low tech system some pazazz.

to the op, idesk is>
sudo apt-get install idesk

---

### Post by kerry_s on 2007-08-12
Never mind, i got it working. even though it said i had xdialog, i did not have it installed.

---

### Post by RedSquirrel on 2007-08-14
> **kike_coello said:**
> hello all, is there a way to modify the menus on fluxbox when you click on the desktop?

Check out the menu howto in my signature. ;)

---

### Post by s26c.sayan on 2007-08-29
If you'd like a menu editor similar in look n feel with the alacarte menu editor common in Gnome, take a look at [Fluxbox Menu Editor (fme)]("http://fluxbox-wiki.org/index.php/Flux_Menu_Editor").

I've included it with my [March Linux]("http://marchlinux.wikidot.com"), and it works very well! :)

---

