---
title: "Xubuntu - Fix Tearing with Nvidia drivers"
date: 2015-07-23
forum: Desktop Environments
---

### Post by jeremy9856 on 2015-07-23
Hello,

I don't know if you saw it but the [tearing with the Nvidia proprietary drivers on Xfce has been fixed !]("http://git.xfce.org/xfce/xfwm4/commit/?id=8a67212860898ef02fee79f64fc774bc14ed769c")
Since I'm using Xubuntu 15.04 and the Nvidia proprietary drivers I want to build xfwm4 and update it properly.

For now this is what I do and that works :
```
$ sudo apt-get install git build-essential xfce4-dev-tools coffeescript pkgconf libgtk2.0-dev libglib2.0-dev libxfce4util-dev libxfce4ui-2-dev libxfconf-0-dev libwnck-dev libxfce4ui-1-dev exo-utils libepoxy-dev
$ git clone git://git.xfce.org/xfce/xfwm4
$ cd xfwm4/
$ export PKG_CONFIG_PATH="$HOME/local/lib/pkgconfig:$PKG_CONFIG_PATH"
$ ./autogen.sh --prefix=$HOME/local && make && make install
- Startup app
    /home/USER/local/bin/xfwm4 --replace &

```

What I want to do is to properly install my build of xfwm4 (create a .deb ?).

How can I do that ?

Thank you

---

### Post by flocculant on 2015-07-25
checkinstall perhaps

```
checkinstall -D make install 
```instead of ```
make install
```

then install it with dpkg

```
dpkg -i foo.deb
```

[https://wiki.debian.org/CheckInstall](https://wiki.debian.org/CheckInstall)
[http://askubuntu.com/questions/240027/how-to-create-a-deb-package-from-compiled-source-files](http://askubuntu.com/questions/240027/how-to-create-a-deb-package-from-compiled-source-files)
[http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/)

---

### Post by jeremy9856 on 2015-09-03
Thank you very much, that works !

This is what I did and it maybe useful to some people :
```
$ sudo apt-get install checkinstall git build-essential xfce4-dev-tools coffeescript pkgconf libgtk2.0-dev libglib2.0-dev libxfce4util-dev libxfce4ui-2-dev libxfconf-0-dev libwnck-dev libxfce4ui-1-dev exo-utils libepoxy-dev
$ git clone git://git.xfce.org/xfce/xfwm4
$ cd xfwm4/
$ ./autogen.sh --prefix=/usr --libdir=/usr/lib/x86_64-linux-gnu/ --disable-debug && make
$ sudo checkinstall -D make install
$ sudo reboot

```

After a reboot no more tearing with Nvidia proprietary drivers. You also have a .deb if you need to reinstall xfwm4.

---

### Post by LastHylian on 2015-09-04
Wow, looks promising. I'm following your instructions, but when I get to 

~$ sudo checkinstall -D make install

I run into the following issues:

```
*** Warning: The package version "4.12.0git.111777d
4.12.0git.111777d
4.12.0git.111777d
4.12.0git.111777d
4.12.0git.111777d" is not a
*** Warning: debian policy compliant one. Please specify an alternate one


dpkg-deb: error: parsing file '/var/tmp/tmp.soycu0ZlPq/package/DEBIAN/control' near line 10 package 'xfwm4':
 empty value for version
/var/tmp/tmp.soycu0ZlPq/dpkgbuild.log (END)
```

Any thoughts?

---

### Post by jeremy9856 on 2015-09-05
You simply have to enter a verison number compliant with debian policy like 4.12.4 and press enter when it hang.

---

### Post by jeremy9856 on 2015-09-05
I noticed that there is some stutter when you play a video.
I opened a bug report and I hope that can be fixed:
[https://bugzilla.xfce.org/show_bug.cgi?id=12189](https://bugzilla.xfce.org/show_bug.cgi?id=12189)

---

### Post by jeremy9856 on 2015-10-05
After some tests I can confirm the stutter is induced by the Systemload, Generic monitor, Sensors plugins when they access to the cpu/gpu/mem load/temp, etc...
So no problem with the Fix for the tearing with Nvidia drivers :)

---

