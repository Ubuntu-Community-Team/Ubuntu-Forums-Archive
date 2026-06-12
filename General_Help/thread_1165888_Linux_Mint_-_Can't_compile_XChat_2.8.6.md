---
title: "Linux Mint - Can't compile XChat 2.8.6"
date: 2009-05-21
forum: General Help
---

### Post by Hetor on 2009-05-21
I'm trying to compile XChat 2.6.8 with a plugin that displays mode chars in userlist instead of spheres. I've already did "sudo apt-get build-dep xchat", but I still get this error:

```
make[3]: *** [fe-gtk.o] Error 1
make[3]: Leaving directory `/home/hetor/xchat/xchat-2.8.6/src/fe-gtk'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/hetor/xchat/xchat-2.8.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/hetor/xchat/xchat-2.8.6'
make: *** [all] Error 2

```

Also, when I'm running ./configure...
```
xchat 2.8.6

Building GTK+ Interface .... : yes
Building TEXT Interface .... : no

PLUGINS: Perl: yes Python: yes TCL: yes

mmx tinting ......... : yes	spelling .............. : libsexy
XShm tinting ........ : no	plugin interface ...... : yes
text backend ........ : pango	nls/gettext ........... : yes
openssl support ..... : yes	ipv6 support .......... : no
dbus support ........ : yes	msproxy ntlm (ISA) .... : no

The binary will be installed in /usr/local/bin

configure complete, now type 'make' and pray.

```

Is it ok that it says: "Building TEXT Interface .... : no"?
Please help me :(

---

### Post by Hetor on 2009-05-21
..Anyone?

---

