---
title: "Pidgin compilation problem"
date: 2007-05-07
forum: Desktop Environments
---

### Post by allanlewis on 2007-05-07
Hi,

I've been trying to compile Pidgin 2.0.0 (final) from source and I'm coming up against a brick wall. Every time I compile (I've tried a few different options) and install - via the usual method:
```

./configure
make
sudo make install

```
...I get the following error when running pidgin:
```

pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory

```
I've searched the forums and Pidgin's Trac site for ages, and can't find anything. I tried editing /etc/ld.so.conf as directed in a forum post, but it didn't help.

Any ideas?

---

### Post by fornix on 2007-05-08
Do you get any errors on make? libpurple is the core library for pidgin. It is compiled with pidgin. In your case probably it isnt being compiled. Chk the console for errors during make.

---

### Post by rich.bradshaw on 2007-05-08
"You must have the GTK+ 2.0 development headers installed to compile Pidgin.
If you only want to build Finch then specify --disable-gtkui when running configure."

How do I stop confgure saying that?

---

### Post by allanlewis on 2007-05-08
> **fornix said:**
> Do you get any errors on make? libpurple is the core library for pidgin. It is compiled with pidgin. In your case probably it isnt being compiled. Chk the console for errors during make.

Ok, will do. I didn't bother going through the whole make history for errors. Is there a way I can get make to output all the stuff that would normally go to the terminal into a text file so I can search it?

---

### Post by ilikeytacos12345 on 2007-05-08
sudo apt-get build-dep gaim

---

### Post by ilikeytacos12345 on 2007-05-08
Read the INSTALL file that comes with the source code.

---

### Post by fornix on 2007-05-08
> Is there a way I can get make to output all the stuff that would normally go to the terminal into a text file so I can search it?

Sure you can do it
```
make >> file.txt
```

---

### Post by fornix on 2007-05-08
Check for errors after ./configure . This would be easier to determine what you are missing for the proper compilation. Usually check the last part of ./configure.

---

### Post by mainalisuyog on 2007-05-08
Why don't u get the .deb package from [www.getdeb.net](www.getdeb.net) ? Easier than compiling.

---

### Post by fakie_flip on 2007-05-08
The idiot who compiled that did not use the ncurses development package to get Finch! Thats a Pidgin without Finch and some crappy configure options. He doesn't know what he's doing. I don't trust third party software, so I compile my own.

---

### Post by allanlewis on 2007-05-09
Ok, I got it sorted. It seems that I simply needed to restart, then it worked... strange. I thought only Windows made you restart for no good reason ;)

Anyway, I've now got it working with Gaim still installed on Edgy. I know this isn't the best situation but I'm shortly going to upgrade to Feisty anyway.

Thanks for all your help!

---

### Post by mdm230 on 2007-08-07
> **ilikeytacos12345 said:**
> sudo apt-get build-dep gaim

worked like a charm. thanks and enjoy your tacos.

---

