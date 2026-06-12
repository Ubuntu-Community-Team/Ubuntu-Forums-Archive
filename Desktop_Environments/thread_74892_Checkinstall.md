---
title: "Checkinstall ?"
date: 2005-10-12
forum: Desktop Environments
---

### Post by dbee on 2005-10-12
I'm trying to make up my own apache .deb files with various mods included.

Everything seems to be going fine ... I get the ./configure out ok, then I make and then I checkinstall - I then usually change the name of the .deb and import it into apt-get.

Unfortunately though, when I try to run the apache packages they don't work ... no explanation at all ... just 

./apachectl  start: httpd could not be started

anybody got any ideas ... I've changed packages and mod's around and I still get the same problem ??

---

### Post by dbee on 2005-10-13
The weird thing is that they run fine when I 

make install

BTW

how do I uninstall apache after a make install ???

---

### Post by TristanMike on 2005-10-13
If it's installed, you should be able to find it via Synaptic, I believe, and remove it that way. Of course you also should be able to do it via the command line with ```
sudo apt-get remove <packagename>
```but if you don't know the exact package name, Synaptic is easier.

---

### Post by dbee on 2005-10-13
Thanks TM,

but unfortunately that'll only work if I installed it via synaptic ... but I did a

make install

so it doesn't show up ... I'm wondering how I do a non-synaptic uninstall ... and I can't find anything in the apache docs that tells me

---

### Post by Wolki on 2005-10-13
[QUOTE=dbee]so it doesn't show up ... I'm wondering how I do a non-synaptic uninstall ... and I can't find anything in the apache docs that tells me[/QUOTE]

First option: try "make uninstall" in the folder where you keep the apache source. Some programs have support for that.
Second option: If that didn't work, and you installed it into /usr/local (usually default) just delete them from there. You might have to be creative with deciding which file belongs where if you have several programs installed this way
Third option: If it's installed in your /usr/ dir directly, you can try the same, but be very careful.
Fourth option: If you break something along the way, reinstall. surest way to get rid of compiled packages.

---

### Post by dbee on 2005-10-13
Thanks wolki,

I was hoping that perhaps there was something more elegant out there than deleting everything ... but alas ... no luck !

---

