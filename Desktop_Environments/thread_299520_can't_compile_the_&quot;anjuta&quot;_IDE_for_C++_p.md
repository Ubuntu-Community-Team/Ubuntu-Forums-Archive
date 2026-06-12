---
title: "can't compile the &quot;anjuta&quot; IDE for C++ programming"
date: 2006-11-14
forum: Desktop Environments
---

### Post by UpsideDownFace on 2006-11-14
I wish to use the "anjuta" Integrated Development Environment for writing and debugging C++ programs.
I downloaded the source code for anjuta-1.2.4 and anjuta-2.0.2.
They both unzipped OK, but when I change into the anjuta-1.2.4 directory and typed "./configure", there were lots of messages and eventually the attatched error messages.
I don't know how or where to get the required libraries.
I have both ubuntu5.10 and ubuntu6.06 and they give very similar results.

 Output from "$./configure 2>anjutaconfig.txt"
configure: error: Package requirements (	glib-2.0 >= 2.0.6 	gtk+-2.0 >= 2.0.8 	ORBit-2.0 >= 2.4.0 	libglade-2.0 >= 2.0.0 	libgnome-2.0 >= 2.0.2 	libgnomeui-2.0 >= 2.0.2 	libgnomeprint-2.2 >= 2.0.1 	libgnomeprintui-2.2 >= 2.0.1 	gnome-vfs-2.0 >= 2.0.2 	gnome-vfs-module-2.0 >= 2.0.2 	libbonobo-2.0 >= 2.0.0 	libbonoboui-2.0 >= 2.0.1 	vte >= 0.7.0 	libxml-2.0 >= 2.4.23 	pango >= 1.1.1) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the ANJUTA_CFLAGS and ANJUTA_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

---

### Post by Ziggurat on 2006-11-14
I think that anjuta 1.2 is on the repositories, you can install it from synaptic,.

For compiling anjuta 2, install all the packages that you have  posted:



libgnomeprint-dev
libgnomevfs-lib
....
....

Hope it helps.

---

### Post by UpsideDownFace on 2006-11-14
> **Ziggurat said:**
> I think that anjuta 1.2 is on the repositories, you can install it from synaptic,.

For compiling anjuta 2, install all the packages that you have  posted:



libgnomeprint-dev
libgnomevfs-lib
....
....

Hope it helps.

I have tried synaptic, and can't find anything about anjuta or the listed packages, so I'm a bit stuck, probably with something very elementary.

---

### Post by Ziggurat on 2006-11-14
I assume you are using edgy, (dapper is similar).

On synaptic, go to Configuratios-> repositories

and check all the checkboxes (the source is unnecessary i think).

Then reload (refresh) like the dialog says and try looking for the packges again.

I checked and anjuta 1.2 is on the repositories.

---

### Post by TheWizzard on 2006-11-14
did you install build-essential? 
this is a meta package with most of the stuff you need to compile.

---

### Post by UpsideDownFace on 2006-11-14
I'm using breezy on my laptop and dapper on my desktop.
I have found anjuta now in "Additionl Packages", but it says it is in universe which doesn't seem to be on my dvd.
I can't yet access the internet with linux, so I seem a bit stuck

---

### Post by UpsideDownFace on 2006-11-14
yes I have done update build-essential to get g++ to work, but I will do it again

---

### Post by TheWizzard on 2006-11-15
> **UpsideDownFace said:**
> I'm using breezy on my laptop and dapper on my desktop.
I have found anjuta now in "Additionl Packages", but it says it is in universe which doesn't seem to be on my dvd.
I can't yet access the internet with linux, so I seem a bit stuck

you need to activate the universe and multiverse repo's manualyy
read 
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
and 
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by UpsideDownFace on 2006-11-15
Thank you very much to TheWizzard.
 The 2 sites you suggest are good, and I followed from monkeyblog.org to cargol.net which says the universe can be downloaded by BitTorrent to dvd images.
 Unfortunately I have now got stuck, as I can't find the repository and don't know how to use BitTorrent. But I am continuing to try!

1/2 hour later; I think I now know how to do these things, and have started BitTorrent. So tomorrow I shall see - I hope.

---

### Post by TheWizzard on 2006-11-16
> **UpsideDownFace said:**
> Thank you very much to TheWizzard.
 The 2 sites you suggest are good, and I followed from monkeyblog.org to cargol.net which says the universe can be downloaded by BitTorrent to dvd images.
 Unfortunately I have now got stuck, as I can't find the repository and don't know how to use BitTorrent. But I am continuing to try!

1/2 hour later; I think I now know how to do these things, and have started BitTorrent. So tomorrow I shall see - I hope.

you don't have to download them. for normal users it is much more convenient just to enable them. then you can download individual packages when you use your package manager.

---

