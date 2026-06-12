---
title: "Seriously? Rezlooks help!"
date: 2009-06-21
forum: General Help
---

### Post by akrchstn on 2009-06-21
Okay so I got gtk 2.8.20 installed and then I downloaded the Rezlooks source files. Went to terminal, put in ```
cd rezlooks-0.6
./configure
make
make install
```And there was no errors, then I went to drag my theme into the theme manager and got this. [IMG]http://i664.photobucket.com/albums/vv4/akrchstn420/fail.png[/IMG]
Seriously, can somebody help.

---

### Post by Legace on 2009-06-21
Download the .deb from [http://www.gnome-look.org/content/show.php?content=39179](http://www.gnome-look.org/content/show.php?content=39179) and double-click on it to install ;)

EDIT: The link seems to be dead. Try this instead: [http://rapidshare.com/files/15311808/rezlooks-0.6_0.6-1_i386.deb](http://rapidshare.com/files/15311808/rezlooks-0.6_0.6-1_i386.deb)

---

### Post by ibuclaw on 2009-06-21
The defaulted prefix of ./configure is the /usr/local directory, so you are installing the engine inside an unmonitored directory.

If you can, uninstall the program (usually '**sudo make uninstall**') then run:
```
./configure --prefix=/usr
```
and then make/install the program again.

Regards
Iain

---

### Post by akrchstn on 2009-06-21
> **Legace said:**
> Download the .deb from [http://www.gnome-look.org/content/show.php?content=39179](http://www.gnome-look.org/content/show.php?content=39179) and double-click on it to install ;)

EDIT: The link seems to be dead. Try this instead: [http://rapidshare.com/files/15311808/rezlooks-0.6_0.6-1_i386.deb](http://rapidshare.com/files/15311808/rezlooks-0.6_0.6-1_i386.deb)

I've already tried the .deb, I get this
```
Selecting previously deselected package rezlooks-0.6.
(Reading database ... 135768 files and directories currently installed.)
Unpacking rezlooks-0.6 (from .../rezlooks-0.6_0.6-1_i386.deb) ...
dpkg: error processing /home/alex/rezlooks-0.6_0.6-1_i386.deb (--install):
 trying to overwrite ' /usr/lib/gtk-2.0/2.4.0/engines/librezlooks.la', which is also in package rezlooks-0.4
Errors were encountered while processing:
 /home/alex/rezlooks-0.6_0.6-1_i386.deb
```And as for tinivole's method, when I run make it says
```
make: Nothing to be done for 'all'
```

EDIT: The theme installed with no errors. Thanks guys.

---

### Post by akrchstn on 2009-06-21
How does one mark a thread as solved

---

### Post by Legace on 2009-06-21
> **akrchstn said:**
> How does one mark a thread as solved

Edit your first post, and all **[SOLVED]** to the post title..

---

