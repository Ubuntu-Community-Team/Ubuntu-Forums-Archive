---
title: "Egoboo invisible-man-like characters o_O'"
date: 2007-05-01
forum: Gaming &amp; Leisure
---

### Post by ]Nbx*cmD[ on 2007-05-01
Hi all,

does anybody know why does this happen to me?

I tried the repository version and the binary one from egoboo's website, had same issue with both.

Thanks!

---

### Post by charlieg on 2007-05-01
There's been updates to Egoboo but not from the official website.

Have a look here:
[http://home.no.net/egoboo/index.html](http://home.no.net/egoboo/index.html)

---

### Post by ]Nbx*cmD[ on 2007-05-01
nice... but where's the linux version?

---

### Post by ]Nbx*cmD[ on 2007-05-01
ping

---

### Post by ]Nbx*cmD[ on 2007-06-18
pong

---

### Post by bodyhead on 2008-03-24
hey I'm having the exact same problem.  No solution yet?

---

### Post by ]Nbx*cmD[ on 2008-03-26
> **bodyhead said:**
> hey I'm having the exact same problem.  No solution yet?

nope...

---

### Post by Jarramundi on 2008-04-18
and I also am having the same problem... Please tell me something has come up.

---

### Post by Zefz on 2008-04-22
Hi, I am the lead designer of the egoboo team. :) Try this:

[http://downloads.sourceforge.net/egoboo/egoboo-data-2.7.5.tar.gz](http://downloads.sourceforge.net/egoboo/egoboo-data-2.7.5.tar.gz) (Data files for Egoboo)

[http://downloads.sourceforge.net/egoboo/egoboo-2.7.5.tar.gz](http://downloads.sourceforge.net/egoboo/egoboo-2.7.5.tar.gz) (Source code for Egoboo)

This is the Development version of Egoboo. It is not the Stable release, but so far we haven't been able to get full Linux support for the Stable version (Which is currently at 2.6.0).


**Egoboo Install Guide for Linux users**
How to compile and install egoboo on Debian/Ubuntu Linux.
(This should work on other linux systems, but the packages (if any) might be different)

Step 1: Make sure you have these packages, and if you don't install them:
* libsdl-image1.2-dev
* libsdl-mixer1.2-dev
* libsdl1.2-dev
* libsdl-ttf2.0-dev
* build-essential

Step 2: Untar the source code.
* Either use a graphical interface or type: tar -xzf egoboo-<version>.tar.gz

Step 3: Open a console (or terminal) and cd to the game directory in the main egoboo folder.
* cd ~/egoboo-<version>/game (Assuming that the directory is in your home folder)

Step 4: Compile the source.
* make -f Makefile.unix

Step 5: Install Egoboo as root. Type:
* sudo make -f Makefile.unix (Ubuntu)
* su -c 'make -f Makefile.unix' (Debian)

Step 6: Get and untar the data.
* Get the egoboo-data-<version>.tar.gz
* Untar it using a graphical interface or using 'tar -xzf egoboo-data-<version>.tar.gz

Step 7: Install the data.
* cd egoboo-data-<version>
* Do specific install steps:
Ubuntu:
* sudo mkdir /usr/share/egoboo
* sudo cp -r * /usr/share/egoboo
Debian:
* su
* mkdir /usr/share/egoboo
* cp -r * /usr/share/egoboo
* exit

Step 8: Create a menu item. (Optional)
** TODO!

Step 9: Start Egoboo! (Mandatory!)
* Either use your menu item or type 'egoboo'.
* Enjoy!

If you experience problems, please ask in the Egoboo Fourms at
[http://egoboo.informe.com/forum/](http://egoboo.informe.com/forum/). Thank you.

---

### Post by Cresho on 2008-05-18
yeah this doesnt work at all.  all install went fine but when I run egoboo, it asks me if I want to install it use apt-get or something.  I tried looking for the egoboo file and it is nowhere in my system after install.  If I install from add-remove, it is fine but I wanted to see the updated one and it does not work at all.

---

