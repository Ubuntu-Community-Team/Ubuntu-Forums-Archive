---
title: "Can't install KTouch on Ubuntu 8.10"
date: 2009-02-22
forum: General Help
---

### Post by amrbekhit on 2009-02-22
Hello all,

I tried to install KTouch on my Ubuntu 8.10 system via the Add/Remove programs but it seems to be unable to download some of the packages. I get the following errors:

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.4.3-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.4.3-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.4.3-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.4.3-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.4.3-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.4.3-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.4.3-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.4.3-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.4.3-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.4.3-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.4.3-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-mysql_4.4.3-0ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qt4-qtconfig_4.4.3-0ubuntu1.1_i386.deb
  404 Not Found



```

Looks like the packages don't exist :S

Any ideas?

--Amr

---

### Post by ashwinhgtx on 2009-02-22
Update your sources first

```
sudo apt-get update
```

Then try to install KTouch again.
```
sudo apt-get install ktouch
```

Besides why do you want to install Ktouch? It's designed for KDE 4. It will have a lot of dependencies. Try out some others like Klavaro, TuxTyping or the terminal based gtypist.

Are you able to install anything else through the Add or Remove programs interface without getting any errors?

---

### Post by amrbekhit on 2009-02-22
Hi ash,

Thanks for your reply - I've installed Klavaro with no problems.

Out of interest, when I tried to install KTouch, there were several packages which were installed - I can see these in the Synaptic history window. Is there an quick way to uninstall these packages, rather than go through them one by one?

Thanks

--Amr

---

### Post by ashwinhgtx on 2009-02-22
I'm not sure if there is an easier way to do that. You can do it through Synaptic or through the command line.

```
sudo apt-get uninstall *paste all the packages you want to remove separated by a space between them*
```

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/apt-get.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/apt-get.html)

Even if you uninstall those packages the configuration files(not very sure of this) will remain on your system. You will have to use the purge option to remove them.
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove)

---

### Post by ben2talk on 2009-09-12
> **ashwinhgtx said:**
> I'm not sure if there is an easier way to do that. You can do it through Synaptic or through the command line.

```
sudo apt-get uninstall *paste all the packages you want to remove separated by a space between them*
```

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/apt-get.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/apt-get.html)

Even if you uninstall those packages the configuration files(not very sure of this) will remain on your system. You will have to use the purge option to remove them.
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove)

This appears to be a bug in the Update Manager - surely if updates are listed, then they should be downloadable from the source?

I just had the same 404 problem, and when I typed 'update' in my terminal, it just went ahead and asked me if I wanted to download them (I previously did 'gedit .bashrc' and added the line [COLOR="Purple"]*alias update='sudo aptitude update && sudo aptitude upgrade'*[/COLOR]

I'm considering - instead of using Super+U to run the update manager, just setting Super+U to run that in the terminal.

---

