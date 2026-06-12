---
title: "Screen corruption when scrolling"
date: 2005-02-12
forum: Desktop Environments
---

### Post by ioliver on 2005-02-12
In a terminal window, scrolling up the screen with mousewheel or scroll thumb works fine. But when you scroll back down, there are blanks bits and loads of text missing. This is worst when using the thumb.

How do I find out what drivers are being used etc. as I guess people will need this info. before they can provide any advice.

Regards

Ian

---

### Post by ioliver on 2005-02-12
A bit of Googling has found the answer. It's a bug that's been in vte for 16 months, and for which a patch exists, but it still hasn't been applied properly upstream.

[http://bugzilla.gnome.org/show_bug.cgi?id=122150](http://bugzilla.gnome.org/show_bug.cgi?id=122150)

That thread gives an interesting insight into the Open Source process when it *doesn't* work!

It looks like it might (just might) get fixed for Gnome 2.10  Still broken in Hoary as of today.

This is the correct patch -
[http://bugzilla.gnome.org/attachment.cgi?id=30677&action=view](http://bugzilla.gnome.org/attachment.cgi?id=30677&action=view)

Regards

Ian

---

### Post by ioliver on 2005-02-13
To fix this I tried the following -

Download and unpack - [http://ftp.gnome.org/pub/GNOME/sources/vte/0.11/vte-0.11.10.tar.bz2](http://ftp.gnome.org/pub/GNOME/sources/vte/0.11/vte-0.11.10.tar.bz2)

Apply patch discussed above to vte.c

Build and install using -
./configure --prefix=/usr --libexecdir=/usr/sbin --disable-gtk-doc &&
make &&
make install

And nothing has changed. But I'm very vague on exactly what install has put where. Was I right to use the configure options that I used? Do I need to rebuild anything else?

Regards

Ian

---

### Post by ioliver on 2005-02-13
Fixed it!!!!

Here is what you need to do -
Download and unpack - [http://ftp.acc.umu.se/pub/GNOME/sources/vte/0.11/vte-0.11.11.tar.bz2](http://ftp.acc.umu.se/pub/GNOME/sources/vte/0.11/vte-0.11.11.tar.bz2)
(I just put it in my home directory)

Make the two changes to src/vte.c as per the patch at - 
[http://bugzilla.gnome.org/attachment.cgi?id=30677&action=view](http://bugzilla.gnome.org/attachment.cgi?id=30677&action=view)

./configure --prefix=/usr --libexecdir=/usr/lib/libvte4 --disable-gtk-doc
make
sudo make install

Test by typing "vte" and doing some scrolling in a maximised window.

Restart any terminal windows you have open - clean scrolling!  Bliss!

However, I'm fairly sure that any hoary updates will hose it again until it gets fixed upstream.

Regards

Ian

---

