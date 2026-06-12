---
title: "Pidgin / Xfire"
date: 2007-08-13
forum: Gaming &amp; Leisure
---

### Post by Mr.NiceGuy on 2007-08-13
i really want pidgin xfire to work i tried using the gusty package from this webiste [http://gfire.sourceforge.net/snapshots/](http://gfire.sourceforge.net/snapshots/)

and when i try the gusty package it says dependency not sitasfiable : libc6

please help me to get this to work:confused:

---

### Post by AnRa on 2007-08-13
Just install libc6! ;)

---

### Post by laforge on 2007-08-13
I tried the same thing he did, but I get the error "Error: Dependency is not satisfiable: libc6".

I tried both "sudo apt-get install libc6" and "sudo apt-get upgrade libc6" and neither did anything.

---

### Post by hikaricore on 2007-08-13
libc6 is installed by default..

The only Ubuntu package for pidgin-xfire I see are for **[B]Gutsy**[/B].
This will not be installable under Feisty.  Nor will the one for Debian.

If you really must have this just download the source:
[http://gfire.sourceforge.net/snapshots/gaim-xfire-0.6.1~20070713.tar.bz2](http://gfire.sourceforge.net/snapshots/gaim-xfire-0.6.1~20070713.tar.bz2)
Which is right above the other links and compile it yourself.

---

### Post by shad0w_walker on 2007-08-13
You should be able to extract the .deb package and copy the files to the plugins folder for pidgin, worked for me.

---

### Post by Mr.NiceGuy on 2007-08-13
> **hikaricore said:**
> libc6 is installed by default..

The only Ubuntu package for pidgin-xfire I see are for **[B]Gutsy**[/B].
This will not be installable under Feisty.  Nor will the one for Debian.

If you really must have this just download the source:
[http://gfire.sourceforge.net/snapshots/gaim-xfire-0.6.1~20070713.tar.bz2](http://gfire.sourceforge.net/snapshots/gaim-xfire-0.6.1~20070713.tar.bz2)
Which is right above the other links and compile it yourself.

I <3 U :)

---

### Post by Mr.NiceGuy on 2007-08-13
configure: error: pkg-config could not locate either libssl.pc or openssl.pc
please make sure you have the development package for openssl/libssl installed
for your distribution. They are usually -dev or -devel packages.



sadly this happened when i did ./configure
can u help me? i tried to install those but it didnt work

---

### Post by Mr.NiceGuy on 2007-08-13
> **shad0w_walker said:**
> You should be able to extract the .deb package and copy the files to the plugins folder for pidgin, worked for me.

im sorry but im a newb at this, but where is the plugins folder for pidgin?

---

### Post by shad0w_walker on 2007-08-13
The plugins for pidgin are should be in the folder:

```
/usr/lib/pidgin
```

The file you want to put in there is something lik

```
libxfire.so
```

It may be slightly diffrent but it should be fairly obvious, i would also copy any other files with xfire in their name to the same folder, just to be sure.

---

### Post by Jammerdelray on 2007-11-27
This is great, Last I heard Pidgin with gfire was not updated, installed the deb file from that link and installed. Works perfectly. So thanks :P:guitar:

---

### Post by 2ndconfused1 on 2010-06-08
yes im grave digging but gfire doesnt work for me, it tells me "connection closed by peer" so yea if anyone knows how to fix that then thx.  i didnt think that i should start a new topic just to ask this.

---

