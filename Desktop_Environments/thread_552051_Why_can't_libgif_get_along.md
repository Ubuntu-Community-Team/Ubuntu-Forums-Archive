---
title: "Why can't libgif get along?"
date: 2007-09-16
forum: Desktop Environments
---

### Post by yang on 2007-09-16
Why does libgif require that all the following packages be removed?

```

$ sudo aptitude install libgif-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libgdiplus 
The following NEW packages will be automatically installed:
  libgif4 
The following packages will be automatically REMOVED:
  libungif4g 
The following NEW packages will be installed:
  libgif-dev libgif4 
The following packages will be REMOVED:
  libungif4g 
0 packages upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/81.1kB of archives. After unpacking 119kB will be used.
The following packages have unmet dependencies:
  libgdiplus: Depends: libungif4g (>= 4.1.4) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libgconf2.0-cil
libgdiplus
libglade2.0-cil
libglib2.0-cil
libgmime2.2-cil
libgnome2.0-cil
libgtk2.0-cil
libmono-system1.0-cil
tomboy

Leave the following dependencies unresolved:
gnome-applets recommends tomboy
ubuntu-desktop recommends tomboy
Score is -3509

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```

---

### Post by j4play on 2007-09-26
yes.  it doesn't seem to be be very friendly unfortunately,

---

### Post by alterpinguin on 2008-01-17
i push this up one more time:
its the same problem with 7.10 ubuntu, still one is forced to use the libungif library or it ends up in a recompile of a lot applications, some big as mplayer, ffmpeg, ...and a lot of smaller programms ... like gtktalog, parts of python-libs, ...

here are links about the time-over of the patent-problems with the gif-format:
general info at slashdot: [http://yro.slashdot.org/article.pl?sid=06/09/29/1657233](http://yro.slashdot.org/article.pl?sid=06/09/29/1657233)
and
special about the LZW compression algo from d***** unisys:
[http://www.unisys.com/about__unisys/lzw](http://www.unisys.com/about__unisys/lzw)

or is there any other easy way (i did not realize) to change from one gif-lib to the other?

thanks, if anyone can shed some light for me to understand the problem.

---

### Post by alterpinguin on 2008-01-18
did not find it last time:
looks like the work to switch to libgif is full in action:

look in here for more information about progress:

[http://ubuntuforums.org/showthread.php?t=669090&highlight=libungif](http://ubuntuforums.org/showthread.php?t=669090&highlight=libungif)

---

