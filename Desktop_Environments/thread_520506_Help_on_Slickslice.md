---
title: "Help on Slickslice"
date: 2007-08-08
forum: Desktop Environments
---

### Post by davidtv on 2007-08-08
I downloaded Slickslice from [http://sourceforge.net/projects/slickslice/](http://sourceforge.net/projects/slickslice/), and the file is now at my desktop. My problem is that I dont know where to go from here... The file has no extension, and I dont know how to install it.

I have installed Mplayer and ImageMagick.

---

### Post by Prefader on 2007-08-08
You don't need to install it, actually.  It's just a shell script, so you only need to run it.  Make sure you've made it executeable (type "chmod +x slickslice-0.6") first, and then try typing ```
./slickslice-0.6
```  and any arguments it requires.  Running it without any arguments looks like it will produce a little help text that will explain how to use it.

---

### Post by davidtv on 2007-08-09
Thanks for answering.

It only says "command not found"...

---

### Post by clblanchard on 2007-08-09
try this.  open a terminal and type

cd ~/Desktop

once at your desktop in the terminal type

sh slickslice-0.6

---

### Post by cx23 on 2007-08-10
Some info you may need here:  [http://slickslice.sourceforge.net/](http://slickslice.sourceforge.net/)

> 
HOW TO USE

To create a timeline of your videofile - execute the following command in a terminal:

$ slickslice -x myweekend_video.avi

That's it. Slickslice will show its progress and then open the image in your favorite jpeg viewer.

HOW TO INSTALL, CONFIGURE AND ENJOY
1) Make sure you have ImageMagick and MPlayer installed.
2) Download and copy the script in your path:
$ sudo cp /where/you/downloaded/slickslice-#.# /usr/local/bin/slickslice
3) Make sure it has the executable attribute set
$ sudo chmod +x /usr/local/bin/slickslice

On its first run SlickSlice will create/update a config file with defaults in your home directory. You may want to examine/update it to your taste later.
$ kwrite ~/.slickslice-config

NOTE: If you like soft thumbnail shadows install ImageMagick version >= 6.3.1


---

### Post by davidtv on 2007-08-10
Thanks a lot! :)

---

### Post by davidtv on 2007-08-10
:( I get this:
```
VERSION: SlickSlice 0.6

INFO: Looking for the programs SlickSlice depends on:
INFO: 'convert' found, 'midentify' NOT found, 'mplayer' found, 'montage' found, 'identify' found
INFO: SlickSlice is powered by ImageMagick & Mplayer packages
INFO: Please install them and try again.
ERROR: Cannot proceed as some programs were not found!
```

When I try sudo apt-get install midentify, it cant find the package. Do you know where I can find it?

---

### Post by davidtv on 2007-08-10
I found it, got it to work, except that it produces only black thumbnails. Guess I gotta play around with it a bit.

Thanks for all help!

---

### Post by PartisanEntity on 2007-09-13
Could you post a link to the 'midentify' script? Thanks

---

### Post by Palmyra on 2007-09-15
> **PartisanEntity said:**
> Could you post a link to the 'midentify' script? Thanks

Echo.  Same issue.

---

### Post by Palmyra on 2007-09-15
> **PartisanEntity said:**
> Could you post a link to the 'midentify' script? Thanks

I have figured it out.  

1.  Open gEdit, and insert the following into it:

 #!/bin/sh
 mplayer -vo null -ao null -frames 0 -identify "$@" 2>/dev/null |
    grep "^ID" |
    sed -e 's/[`\\!$"]/\\&/g' |
    sed -e '/^ID_FILENAME/ { s/^ID_FILENAME=\(.*\)/ID_FILENAME="\1"/g;
  }'

2.  Save it in /usr/bin/ as midentify.  Of course, you'll need sudo privileges (gksudo gedit after pressing ALT-F2 to open gEdit in sudo mode).

3.  cd into /usr/bin/ by typing, obviously, cd /usr/bin/.

4.  To make it an executable, type sudo chmod +x midentify.

Done.  Slickslice should no longer complain.

---

### Post by PartisanEntity on 2007-09-16
Thanks Palmyra but I ended up getting it from [here]("http://ubuntuforums.org/showthread.php?t=551030").

---

