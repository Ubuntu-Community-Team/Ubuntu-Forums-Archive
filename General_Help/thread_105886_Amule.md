---
title: "Amule"
date: 2005-12-19
forum: General Help
---

### Post by ubuntuubuntu on 2005-12-19
I installed aMule with Synaptic. When I go to Applications --> Internet --> aMule, I click on aMule and it' s not openned. I've reinstalled aMule and the problem still occurs. Whart should I do?

---

### Post by yaztromo on 2005-12-21
Try running amule from a terminal. Do you see any errors?

---

### Post by ubuntuubuntu on 2005-12-27
[QUOTE=yaztromo]Try running amule from a terminal. Do you see any errors?[/QUOTE]
No error is shown.

---

### Post by sciurus on 2005-12-27
[QUOTE=ubuntuubuntu]No error is shown.[/QUOTE]

What happens?

---

### Post by ubuntuubuntu on 2005-12-29
I'm sorry. It does give an error message: 
./amule: error while loading shared libraries: libbfd-2.15.so: cannot open shared object file: No such file or directory

---

### Post by grte on 2005-12-29
You'll have to install those libraries, it looks like.  Just search for them in Synaptic, install them, and you should be good to go.

---

### Post by ubuntuubuntu on 2005-12-29
I can't find them in Synaptics.

---

### Post by grte on 2005-12-29
[QUOTE=ubuntuubuntu]I can't find them in Synaptics.[/QUOTE]

Try looking for binutils-dev.

Or alternately, in the terminal,

```
sudo apt-get install binutils-dev
```

It *should* work.

---

### Post by sciurus on 2005-12-29
I prefer to have the amule daemon and GUI running as seperate processes. If you'd like to do that:

1) sudo apt-get install build-essential checkinstall libcurl3-dev libpng12-dev libgd2-noxpm-dev libwxgtk2.6-dev libgtk2.0-dev
2) cd ~
3) wget [http://ovh.dl.sourceforge.net/sourceforge/amule/aMule-2.0.3.tar.gz](http://ovh.dl.sourceforge.net/sourceforge/amule/aMule-2.0.3.tar.gz)
4) tar xvf aMule-2.0.3.tar.gz
5) cd aMule-2.0.3 
6) ./configure --enable-amulecmd --enable-webserver --enable-cas --disable-monolithic --enable-amule-daemon  --enable-amule-gui
7) sudo checkinstall make install
8 ) amuled, then hit ctrl-c to kill it
9 ) You need to set a password for the GUI to use to connect to the daemon. The md5 hash of this password is stored in the configuration file after ECPassword, so use *echo -n putthepasswordhere | md5sum | cut -d ' ' -f 1* to ge the hash.
10) nano ~/.aMule/amule.conf
11) [ExternalConnect]
AcceptExternalConnections=1
ECUseTCPPort=1
ECPassword=
12) amuled &
13) amulegui &

---

### Post by yaztromo on 2005-12-30
libbfd is part of binutils. But the version that comes with this package is libbfd 2.16.1.

I dont have libbfd 2.15 on my system yet amule does not complain, how strange :???: 

Anyway, if installing binutils-dev does not help, you could try creating a symlink in /usr/lib called libbfd-2.15.so that points to libbfd-2.16.1.so

I'm not very good with these things so someone correct me if this is wrong:

```
sudo ln -s /usr/lib/libbfd-2.16.1.so /usr/lib/libbfd-2.15.so
```

---

### Post by makhand on 2006-01-23
[QUOTE=sciurus]I prefer to have the amule daemon and GUI running as seperate processes. If you'd like to do that:
[/QUOTE]

Except for sourceforge seems to be down for the moment. The thing i dont understand is why amuled is not built-in automatically when you install the package from synaptic. Is there a way to request this?

---

