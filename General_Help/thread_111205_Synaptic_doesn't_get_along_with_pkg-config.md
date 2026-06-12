---
title: "Synaptic doesn't get along with pkg-config"
date: 2006-01-01
forum: General Help
---

### Post by escape on 2006-01-01
When I install various libraries through synaptic, it doesn't put corresponding .pc files in /usr/lib/pkg-config.

I really just want to install gaim2.0 and a couple other apps that don't have .deb installers yet, but it thinks glib >= 2.0 is not installed. It IS installed; I have every version of gcc/gnu/glib availble on synaptic installed, but unfortunately there's no glib2.0.pc equivalent file showing up in /usr/lib/pkgconfig. 

I ended up trying to install from gtk.org, but I get the same issue with any dependency I install through synaptic - pango, atk, cairo, libpng, ligjpeg, xorg, etc are all installed (either by ubuntu or me) but they have no .pc file and are thus not recognized by the ./configure of other programs that depend on them.  The .pc files *are* created though when I download a .tar.gz version of them and conifgure->make->make install. 

What am I missing here? On a previous install of Breezy Badger (which is what I am currently using), I was able to get this to work just through synaptic, but not anymore. Could it be some option I did in configuring the install? Is it something with the new kernel for Breezy (10)? Or is it just something with synaptic...

edit - this is a fresh install of breezy

---

### Post by sciurus on 2006-01-02
I've never heard of a .pc file, don't have a /usr/lib/pkg-config directory,and have built software from source. The worst I ever have to do is specify a library path as an argument to a configure script.

---

### Post by escape on 2006-01-02
My bad, it was /usr/lib/pkgconfig. I can download sources, but it takes less time to use synpatic than to download, tar gxvf, and make the source, so I'd prefer synaptic. I think I'm just going to try reformatting..

---

