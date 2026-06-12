---
title: "Problems compiling Ktorrent"
date: 2006-02-03
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-02-03
So, I downladed Ktorrent [(http://kde-apps.org/content/show.php?content=26353)]("http://kde-apps.org/content/show.php?content=26353")

After I've run ./configure, I get a message to run make. So i run "sudo make", but at the end, I turn out with a few errors, and here's the output:

> 
...
...
/usr/share/qt3/include/private/qucom_p.h:69: warning: 'struct QUBuffer' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:77: warning: 'struct QUType' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:104: warning: 'struct QUType_Null' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:287: warning: 'struct QUType_enum' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:307: warning: 'struct QUType_ptr' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:326: warning: 'struct QUType_iface' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:345: warning: 'struct QUType_idisp' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:364: warning: 'struct QUType_bool' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:383: warning: 'struct QUType_int' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:403: warning: 'struct QUType_double' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:423: warning: 'struct QUType_charstar' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:444: warning: 'struct QUType_QString' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:65: warning: 'struct QUType_QVariant' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:87: warning: 'struct QUType_varptr' has virtual functions but non-virtual destructor
/bin/sh ../libtool --silent --mode=link --tag=CXX g++  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -fexceptions     -o libktorrent.la -rpath /usr/lib -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib -L/usr/X11R6/lib -L/usr/share/qt3/lib -L/usr/lib  pluginmanager.lo functions.lo expandablewidget.lo pluginmanagerprefpage.lo pluginmanagerwidget.lo pluginmanagerprefpage.moc.lo  ../libktorrent/migrate/libmigrate.la ../libktorrent/util/libutil.la ../libktorrent/torrent/libtorrent.la ../libktorrent/kademlia/libkademlia.la ../libktorrent/interfaces/libinterfaces.la -lkparts
grep: /lib/libacl.la: No such file or directory
/bin/sed: can't read /lib/libacl.la: No such file or directory
libtool: link: `/lib/libacl.la' is not a valid libtool archive
make[3]: *** [libktorrent.la] Error 1
make[3]: Leaving directory `/home/stian/Desktop/ktorrent-1.2/libktorrent'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/stian/Desktop/ktorrent-1.2/libktorrent'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/stian/Desktop/ktorrent-1.2'
make: *** [all] Error 2
stian@stian:~/Desktop/ktorrent-1.2$ 

Based on the output, I can't seem to figure out what the problem is? Perhaps its obvious but im a little new to Ubuntu.


(I managed to compile and install it on my laptop which is also running Kubuntu, so I'm obviously missing something, help would be appreciated. Thanks.

---

### Post by darknightuk on 2006-02-03
think u need to install libacl1-dev, could be wrong i'm new to this aswell if u get a compile error like that with anything seems to be a dev package missing

---

### Post by GeneralZod on 2006-02-03
[QUOTE=darknightuk]think u need to install libacl1-dev, could be wrong i'm new to this aswell if u get a compile error like that with anything seems to be a dev package missing[/QUOTE]

This would be my guess, but I can't find any packages that provide that exact file.  Add libacl1 as well.

Also, it's too late now but you should not run "make" as sudo.  It's not necessary, and can lead to annoying problems :)

---

### Post by raggamuffin on 2006-02-03
why don't you just 'sudo apt-get install ktorrent'?...it's in the universe repos...

---

### Post by stiankarlsen on 2006-02-03
I added libacl1-dev and libacl1, but the problem remains the same.


(Of course I could use apt-get install ktorrent, but i want my system to be able to compile it from source as well)

---

### Post by GeneralZod on 2006-02-03
[QUOTE=stiankarlsen]
(Of course I could use apt-get install ktorrent, but i want my system to be able to compile it from source as well)[/QUOTE]

Plus, the version in the official repos/ backports is way out of date :)

I'm not sure what's wrong here as I've been compiling from SVN recently without any problems.  I'll try the "official" 1.2 release at some point.

Oh, and try out

```

sudo apt-get build-dep ktorrent

```

just in case.

---

### Post by stiankarlsen on 2006-02-04
Still can't compile, I am open to suggestions.

---

### Post by Peter41az on 2006-02-05
can you not just go to ktorrent.pwsp.net, download the i386 deb package, and in terminal do sudo dpkg -i ktorrent_1.2-1_i386.deb ? that should give you 1.21, the latest version? i just did so and it worked fine.

---

### Post by GeneralZod on 2006-02-05
[QUOTE=stiankarlsen]Still can't compile, I am open to suggestions.[/QUOTE]

Hmmm...very odd.  I tried it here and it compiles fine. Sorry, I can't be of any further help :/

Rou might want to just nuke that entire directory, ensure that you have done the "sudo build-dep ktorrent" thing, re-extract the source and this time do ./configure and make *without* using sudo.

---

### Post by Jucato on 2006-02-05
Is Ktorrent better now? Last time I installed it (from the repos), it was very strange. It didn't download directly to a specific directory (downloads to a temporary directory then transfers to another after it has finished). It also completely deleted any downloaded files if you remove the corresponding torrent from it's download list.

---

### Post by GeneralZod on 2006-02-05
[QUOTE=Fenyx]Is Ktorrent better now? Last time I installed it (from the repos), it was very strange. It didn't download directly to a specific directory (downloads to a temporary directory then transfers to another after it has finished). It also completely deleted any downloaded files if you remove the corresponding torrent from it's download list.[/QUOTE]

You can now import existing torrents and carry on where you left off/ seed them, and are given the option of where to put your torrent when you start it up.  If you've had files deleted, though, I'd probably make sure you have backups of any files you want to use, just in case.  Last time I looked, removing an *incomplete* torrent from the list brings up a dialog giving you the option to delete all files.  I think this took me by surprise once and I just clicked "Yes", thinking it was a standard "Are you sure you want to remove this torrent?" dialog box.  Whoops :)

---

### Post by stiankarlsen on 2006-02-05
Fenyx, Ktorrent is alot better now yes.

Using the deb package is definetely an option, but I just can't shake the feeling of not being able to compile, it's annoying as all h***.

---

### Post by Peter41az on 2006-02-05
Yeah i know what you mean. SO far, no problems tho. It was late and my fingers hurt, so Deb it was heh. actually i just used the 1.2 from deb, its pretty sweet.

---

### Post by Jucato on 2006-02-05
Hmm... that's good news then. I've always been looking for a good but lightweight alternative to Bittorrent (the latest version, w/c is the best for me). BitTornado just doesn't cut it for me and qtorrent is still quite young (i think, at least the repo version). Thanks for the info. might try it out tomorrow and download the .deb. Still too scared to compile stuff on my own. :D

---

### Post by stiankarlsen on 2006-02-07
Im guessing nobody have figured out what my original problem could be?

---

### Post by Jucato on 2006-02-07
did you try downloading the tar.gz directly from the KTorrent website? You could also try to delete the entire untarred KTorrent directory, and untar it again, just to start from a clean start. Is build-essential and gcc up-to-date? I'm sorry if I can't be of more help. It installed fine on my system. you could also try asking in the KTorrent forums for help. 

It might be worth the effort, because KTorrent is quite nice, after you get used to the unconventional way it handles torrents. It offers almost all the basic features of Azureus and BitTornado, plus it's not a resource hog.

---

