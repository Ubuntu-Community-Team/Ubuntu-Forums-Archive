---
title: "DVDstyler and GNOME"
date: 2006-02-01
forum: Desktop Environments
---

### Post by Schmic on 2006-02-01
I am having alot of problems getting any dvd authoring programs to run properly atm (to make menu's). I have tried a few and DVDstyler has been the closest so far. 

I am new to linux so i need the gui because trying to learn xml to make my own menu's is a bit beyond me atm.

I can get DVDstyler to run and create my menu's then about 5 seconds after i start the creation of the dvd, DVDstyler crashes without any messages. After running it from terminal i have managed to retrieve this:

```
(dvdstyler:10287): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
Segmentation fault
```

Can anyone help me out here please. Is this caused by the mjpegtools problem that i have seen in other posts or is it because i am using Gnome instead of KDE?

I have seen mention of other programs for authoring but they mostly seem to be for KDE not Gnome or does this not make a difference?

---

### Post by fsman on 2006-02-01
I don't know how you installed your dvdstler. I added the following line to my apt sources.list

deb [http://dvdstyler.sourceforge.net/repository/ubuntu/](http://dvdstyler.sourceforge.net/repository/ubuntu/) breezy main

then installed dvdstyler via synaptic.

no problems with dvdstyler at all on Ubuntu.
:)

---

### Post by Schmic on 2006-02-02
I installed the same way except i used apt-get instead of synaptic (same thing really)

I did install automatix prior to it though, maybe there is a conflict in there somewhere?

edit: fixed my problem, i found something in the DVDstyler wiki and thought i would try it

> There is a problem with mjpegtools >1.6.2 by menu generating.
To fix it you need to add "-S 420mpeg2" to ppmtoy4m command
in DVDStyler core settings or downgrade mjpegtools.

that seemed to have fixed it \\:D/

---

### Post by fsman on 2006-02-02
yep - I remember doing that myself. Well done =D>

---

### Post by Haegin on 2006-02-26
Whenever I run dvdstyler (after installing it through apt-get as you said) I just get the following:
```

harry@geswick:/tmp$ dvdstyler
Fatal Error: Mismatch between the program and library build versions detected.
The library used 2.6 (no debug,Unicode,compiler with C++ ABI 102,wx containers,compatible with 2.4),
and your program used 2.6 (no debug,Unicode,compiler with C++ ABI 1002,wx containers,compatible with 2.4).
Aborted

```
Any ideas?

---

