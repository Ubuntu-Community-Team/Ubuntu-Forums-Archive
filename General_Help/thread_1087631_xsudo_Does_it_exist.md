---
title: "xsudo? Does it exist?"
date: 2009-03-05
forum: General Help
---

### Post by mikeym on 2009-03-05
Hi,

OK first I'd better confess that I'm not running ubuntu on this machnie (although my main machine has always been ubuntu), but I thought I might get some sensible answers over here. 

I had to switch to Gentoo on my old PPC because I found that the Ubuntu community PPC wasn't sutting it any more and I had heard that Gentoo PPC was still supported. 

I'm running openbox with mostly GTK applications (although I have Qt3 for Opera) I have neither Gnome or KDE installed, but my question is how do I get su privalages without upening a terminal? 

Everything I see tells me that i should use gksudo or the KDE equivelent but that would require installing Gnome or KDE - quite a price for a password window. I fould some mention of consolehelper and PAM but these appear to be only for redhat. 

Is there any xsudo program that is independant of the DEs?

---

### Post by mikeym on 2009-03-05
* Bump *

Found something called xsu which is now called gnomesu and depends on the gnome base as well.

---

### Post by HermanAB on 2009-03-05
gksudo

Cheers,

Herman

---

### Post by mikeym on 2009-03-05
Unfortunately as I was saying I don't want to install the entire of gnome to get gksudo. It seems overkill. 

Anything else?

---

### Post by mb_webguy on 2009-03-05
You would use gksudo in Xubuntu, and it doesn't have Gnome installed.  The gksu package depends on a few gtk libraries (e.g. libcairo2, libgtk2, libglib2, etc.) and gnome-keyring (which itself depends on a few additional libraries), but not the entire Gnome desktop environment.

---

