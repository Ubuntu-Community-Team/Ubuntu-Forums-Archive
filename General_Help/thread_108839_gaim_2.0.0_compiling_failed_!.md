---
title: "gaim 2.0.0 compiling failed !"
date: 2005-12-27
forum: General Help
---

### Post by drfalkor on 2005-12-27
I tryed to compile gaim(2.0.0 cvs) like this:
./configure --enable-gnutls=yes

_But then I got this error:_
--------------------------------------
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.8.0, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at [http://www.gtk.org/](http://www.gtk.org/).
--------------------------------------
What now ? :confused: :???:

EDIT: I dont have the /etc/ld.so.conf file

EDIT2: What distro "loves" compiling ? (everything else than gentoo) :P

---

### Post by Vectrox on 2005-12-27
Distributions who loves compiling:

Gentoo
Arch linux
Slackware
Linux From Scratch
Onebase Linux
Sorcerer
Lunar Linux

And many more..

---

### Post by ykpaiha on 2005-12-27
Sorry to be late but a nice howto exist here:
[http://www.ubuntuforums.org/showthread.php?t=100899&highlight=gaim](http://www.ubuntuforums.org/showthread.php?t=100899&highlight=gaim)
No problem at all to compile gaim!!
sometime the solution is not inside the computer ....

---

### Post by fordfan753 on 2005-12-27
Try running
```
sudo ldconfig
```
does that help at all?

---

### Post by drfalkor on 2005-12-28
Well, I did a fresh install of the distro and installed the dev packages again, then it worked smooth and nice- weard it dint work before.
thanks for your help ! :p

---

### Post by drfalkor on 2005-12-28
Here is another "problem" Im getting now, when I try to compile gaim!

./configure --enable-gnutls=yes
```
gaim 2.0.0beta1

Build Protocol Plugins........ : yes
Protocols to link statically.. :
Protocols to build dynamically : gg irc jabber msn novell oscar simple yahoo zephyr

UI Library.................... : GTK+ 2.x
SSL Library/Libraries......... : GNUTLS

Build with Plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : no
Build with Tcl support........ : no
Build with Tk support......... : no
Build with Audio support...... : no
Build with GtkSpell support... : no
Build with Voice/Video support : no
Build with DBUS support....... : no
Build with Cyrus SASL support. : no
Has you....................... : yes


Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no

Use XScreenSaver Extension.... : no
Use X Session Management...... : no
Use startup notification.......: no

Print debugging messages...... : no

Gaim will be installed in /usr/local/bin.

configure complete, now type 'make'

```
the configure is completed, now I type 'make' (the "making" went well, I think)...

But, here comes the "problem", when I type 'sudo make install'
```
falkor@ubuntu:~/Desktop/gaim-2.0.0beta1$ sudo make install
Making install in doc
make[1]: Entering directory `/home/falkor/Desktop/gaim-2.0.0beta1/doc'
make[2]: Entering directory `/home/falkor/Desktop/gaim-2.0.0beta1/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/man/man1" || mkdir -p -- "/usr/local/man/man1"
mkdir: cannot create catalog &#171;/usr/local/man&#187;: File exist
make[2]: *** [install-man1] Error 1
make[2]: Leaving directory `/home/falkor/Desktop/gaim-2.0.0beta1/doc'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/falkor/Desktop/gaim-2.0.0beta1/doc'
make: *** [install-recursive] Error 1
falkor@ubuntu:~/Desktop/gaim-2.0.0beta1$

``` 

any clue on whats going on here ? :confused:

EDIT: I had to translate: "cannot create catalog and File exist" to english from norwegian - so you guys can understand (I know, My english is crappy)

---

### Post by Zelut on 2005-12-28
try the wiki I wrote on compiling gaim from source.  Seems to work everytime... [http://wiki.ubuntu.com/CompileGaim](http://wiki.ubuntu.com/CompileGaim)

---

### Post by drfalkor on 2005-12-28
sudo apt-get build-dep gaim (everything installs OK)
sudo apt-get install libgnutls10-dev (I already have, libgnutls11-dev)
sudo apt-get install libgtk2.0-0 libgtk2.0-dev (I have both of them in the latest version)

I mv the gaim.tar.gz to the /tmp/ folder, and then I did:

cd /tmp/

tar zxvf gaim.tar.gz

cd gaim[version]

sudo ./configure --enable-gnutls=yes
```
gaim 2.0.0beta1

Build Protocol Plugins........ : yes
Protocols to link statically.. :
Protocols to build dynamically : gg irc jabber msn novell oscar simple yahoo zephyr

UI Library.................... : GTK+ 2.x
SSL Library/Libraries......... : Mozilla NSS and GNUTLS

Build with Plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : no
Build with Tcl support........ : yes
Build with Tk support......... : yes
Build with Audio support...... : yes
Build with GtkSpell support... : yes
Build with Voice/Video support : no
Build with DBUS support....... : no
Build with Cyrus SASL support. : no
Has you....................... : yes


Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no

Use XScreenSaver Extension.... : yes
Use X Session Management...... : yes
Use startup notification.......: yes

Print debugging messages...... : no

Gaim will be installed in /usr/local/bin.

configure complete, now type 'make'

```

ok, now I type:

sudo make (I could not see any errors here, I think)

and then I did the:

sudo make install

well, here is our old buddy again:
```
falkor@ubuntu:/tmp/gaim-2.0.0beta1$ sudo make install
Making install in doc
make[1]: Entering directory `/tmp/gaim-2.0.0beta1/doc'
make[2]: Entering directory `/tmp/gaim-2.0.0beta1/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/man/man1" || mkdir -p -- "/usr/local/man/man1"
mkdir: kan ikke opprette katalog &#171;/usr/local/man&#187;: Filen eksisterer
make[2]: *** [install-man1] Error 1
make[2]: Leaving directory `/tmp/gaim-2.0.0beta1/doc'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/tmp/gaim-2.0.0beta1/doc'
make: *** [install-recursive] Error 1
falkor@ubuntu:/tmp/gaim-2.0.0beta1$

```
:confused: :eek: 
Thanks for your help !

---

### Post by fordfan753 on 2005-12-28
I think there's a make option to ignore errors, and keep going, I don't remember what it is, sometimes it'll help, but sometimes it'll just fail on something else or wont install properly, it doesn't want to install because there's already something in one of the directories it's trying to write to or something.

---

### Post by drfalkor on 2005-12-28
wtf ? after a restart... I could: sudo make install nice and clean :D:D thank you guys for helping me!:p

---

