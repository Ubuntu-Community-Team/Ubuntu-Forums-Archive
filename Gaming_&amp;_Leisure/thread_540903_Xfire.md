---
title: "Xfire"
date: 2007-09-02
forum: Gaming &amp; Leisure
---

### Post by Hydralore on 2007-09-02
Hey, i just got Ubuntu and i wanted to install Xfire, just to chat to friends, but after following many threads and trying many different things, i have no idea whats different. I tried installing a program called Gaim but there was no difference on my desktop or in the applications menu so i dont know if it installed properly or not. I followed this tutorial 
```
http://ubuntuforums.org/showthread.php?t=226456&highlight=xfire
```
and all the commands seemed to work, but i see no difference on the desktop or in the applications menu. how do i run gfire? or has it not installed properly

sorry, im a complete newbie to ubuntu, i hope you guys can help me ^^ 
thanks in advance

edit : i got Gaim installed, but i cant get the xfire plugin to work ^^

edit 2 : when i type  ./configure --prefix=/usr
i get ```
 Configuration complete

Debugging enabled..............: no
Using gaim version.............: 2.0
Gaim package prefix............: /usr
Gaim package libdir............: /usr/lib
Install prefix.................: /usr
Install libdir.................: /usr/lib
Gaim lib dir detected..........: Yes


Type make to compile

Make sure you copy data/gfire_games.xml to /home/hydralore/.gaim/

```

but then when i type  make  something goes wrong.
```
hydralore@hydralore-D:~/Desktop/gaim-xfire-0.6.04$ make
make  all-recursive
make[1]: Entering directory `/home/hydralore/Desktop/gaim-xfire-0.6.04'
Making all in src
make[2]: Entering directory `/home/hydralore/Desktop/gaim-xfire-0.6.04/src'
/bin/bash ../libtool --silent --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..  -DLIBDIR=\"/usr/lib/gaim/\"      -DDATADIR=\"/usr/share\"        -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/include/gaim -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include                    -Wall -g3 -c gfire.c
gfire.c: In function 'gfire_login':
gfire.c:353: warning: passing argument 2 of 'gaim_proxy_connect' from incompatible pointer type
gfire.c:353: warning: passing argument 3 of 'gaim_proxy_connect' makes pointer from integer without a cast
gfire.c:353: warning: passing argument 4 of 'gaim_proxy_connect' makes integer from pointer without a cast
gfire.c:353: warning: passing argument 5 of 'gaim_proxy_connect' from incompatible pointer type
gfire.c:353: error: too few arguments to function 'gaim_proxy_connect'
gfire.c: At top level:
gfire.c:1498: warning: initialization from incompatible pointer type
make[2]: *** [gfire.lo] Error 1
make[2]: Leaving directory `/home/hydralore/Desktop/gaim-xfire-0.6.04/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/hydralore/Desktop/gaim-xfire-0.6.04'
make: *** [all-recursive-am] Error 2
hydralore@hydralore-D:~/Desktop/gaim-xfire-0.6.04$ 

```

---

### Post by Hydralore on 2007-09-02
i should add that im using 

 Ubuntu 7.04, Feisty Fawn

and gaim 2.0.0 beta 6

---

### Post by Cappy on 2007-09-02
GAIM Install:
[http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb](http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb)

(taken from [http://ubuntuforums.org/showthread.php?t=504661](http://ubuntuforums.org/showthread.php?t=504661))

---

Customization on launching games and setting your "in-game" status:
[http://ubuntuforums.org/showthread.php?t=397255](http://ubuntuforums.org/showthread.php?t=397255)

---

### Post by Hydralore on 2007-09-02
thanks, but i still have no idea what to do to get it to work :S


edit : its says its wrong architecture 'i386'

---

### Post by Cappy on 2007-09-02
You're using 64-bit (like me).

Well you can try my own package which is the first package I ever tried making:
[http://www.boundlesssupremacy.com/Cappy/gfire/gaim-xfire_0.6.1~20070308-1_amd64_GPL.deb](http://www.boundlesssupremacy.com/Cappy/gfire/gaim-xfire_0.6.1~20070308-1_amd64_GPL.deb)

-or-

You should use a newer version of the source to compile:
[http://gfire.sourceforge.net/snapshots/gaim-xfire-0.6.1~20070308.tar.bz2](http://gfire.sourceforge.net/snapshots/gaim-xfire-0.6.1~20070308.tar.bz2)

I think it will be something like
```

sudo apt-get install libssl-dev gaim-dev

```
```

PKG_CONFIG_PATH=/usr/lib/pkgconfig/
export PKG_CONFIG_PATH 
./configure --prefix=/usr

```

Hopefully something will work ^^

You'll need to restart GAIM and go to Accounts--> Add/Edit
click the "Add" button and if "Xfire" shows up as a network choice you have it working!



Edit:
Someone else compiled gfire for 64-bit here:
[http://ubuntuforums.org/showpost.php?p=3004480&postcount=61](http://ubuntuforums.org/showpost.php?p=3004480&postcount=61)

---

### Post by Hydralore on 2007-09-02
thanks alot, its showing now.. 

hopefully iv learned from this, haha :D

---

