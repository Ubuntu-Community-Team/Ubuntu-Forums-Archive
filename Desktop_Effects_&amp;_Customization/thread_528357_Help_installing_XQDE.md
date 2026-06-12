---
title: "Help installing XQDE"
date: 2007-08-17
forum: Desktop Effects &amp; Customization
---

### Post by jcmorales85 on 2007-08-17
I'm interested in installing XQDE (looks like a kxdocker upgrade) and am unable to do so.

the read me file says this:  

Hello this is aplha testing of XQDE
you can mail to [email]xqde@xiaprojects.com[/email]
or search for support on xqde.xiaprojects.com

- DO NOT ASK for HOW TO CONFIGURE IT!
- enjoy as is... next time will be better!
- new binary release will come on next days stay tuned!

This is only a test purpose software!
Requirements:
- Composite manager
- Qt4.2

How to install
- There is no install at this time! simply move xqde folder to your home:
/home/foo/.xqde
start xqde binary!

- if you move a .xml from basket to template will be used as template for
  this kind of class...
- there are 2 or 3 known bugs... anyway report own...
- if you cannot find your suitable binary release mail us we try to compile a
  working version for you!




What do you need:
i686 32bit Linux
kernel-2.6.x
Fully working Composite environment like Beryl or Compiz with effects ;)


Here is the compiilation lib:

        libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb7efd000)
        libQtXml.so.4 => /usr/lib/qt4/libQtXml.so.4 (0xb7ebd000)
        libQtGui.so.4 => /usr/lib/qt4/libQtGui.so.4 (0xb784f000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7805000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7669000)
        libQtNetwork.so.4 => /usr/lib/qt4/libQtNetwork.so.4 (0xb7612000)
        libQtCore.so.4 => /usr/lib/qt4/libQtCore.so.4 (0xb74a6000)
        libstdc++.so.6 => /usr/lib/gcc/i686-pc-linux-gnu/4.1.1/libstdc++.so.6 (0xb73a0000)
        libm.so.6 => /lib/libm.so.6 (0xb737c000)
        libgcc_s.so.1 => /usr/lib/gcc/i686-pc-linux-gnu/4.1.1/libgcc_s.so.1 (0xb7372000)
        libc.so.6 => /lib/libc.so.6 (0xb7251000)
        /lib/ld-linux.so.2 (0xb7f1e000)

If you get this error:
$ ./xqde
./xqde: symbol lookup error: ./xqde: undefined symbol: _ZN9QListData7detach2Ev
Try manually compile sources! (We are buinding new fixed binaries)


can anyone help me?

---

### Post by lilfuzz on 2007-09-04
> **jcmorales85 said:**
> I'm interested in installing XQDE (looks like a kxdocker upgrade) and am unable to do so.

the read me file says this:  

Hello this is aplha testing of XQDE
you can mail to [email]xqde@xiaprojects.com[/email]
or search for support on xqde.xiaprojects.com

- DO NOT ASK for HOW TO CONFIGURE IT!
- enjoy as is... next time will be better!
- new binary release will come on next days stay tuned!

This is only a test purpose software!
Requirements:
- Composite manager
- Qt4.2

How to install
- There is no install at this time! simply move xqde folder to your home:
/home/foo/.xqde
start xqde binary!

- if you move a .xml from basket to template will be used as template for
  this kind of class...
- there are 2 or 3 known bugs... anyway report own...
- if you cannot find your suitable binary release mail us we try to compile a
  working version for you!




What do you need:
i686 32bit Linux
kernel-2.6.x
Fully working Composite environment like Beryl or Compiz with effects ;)


Here is the compiilation lib:

        libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb7efd000)
        libQtXml.so.4 => /usr/lib/qt4/libQtXml.so.4 (0xb7ebd000)
        libQtGui.so.4 => /usr/lib/qt4/libQtGui.so.4 (0xb784f000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7805000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7669000)
        libQtNetwork.so.4 => /usr/lib/qt4/libQtNetwork.so.4 (0xb7612000)
        libQtCore.so.4 => /usr/lib/qt4/libQtCore.so.4 (0xb74a6000)
        libstdc++.so.6 => /usr/lib/gcc/i686-pc-linux-gnu/4.1.1/libstdc++.so.6 (0xb73a0000)
        libm.so.6 => /lib/libm.so.6 (0xb737c000)
        libgcc_s.so.1 => /usr/lib/gcc/i686-pc-linux-gnu/4.1.1/libgcc_s.so.1 (0xb7372000)
        libc.so.6 => /lib/libc.so.6 (0xb7251000)
        /lib/ld-linux.so.2 (0xb7f1e000)

If you get this error:
$ ./xqde
./xqde: symbol lookup error: ./xqde: undefined symbol: _ZN9QListData7detach2Ev
Try manually compile sources! (We are buinding new fixed binaries)


can anyone help me?

you will need Qt4.2 packages (avil in fesity repos), and Beryl or Compiz (Feisty comes with compiz) in order to execute the binary. After I got all the stuff together, I ran it on command line and got the bit where he says:

> If you get this error:
$ ./xqde
./xqde: symbol lookup error: ./xqde: undefined symbol: _ZN9QListData7detach2Ev
Try manually compile sources! (We are buinding new fixed binaries)


So since I also had QT dev packages, I downloaded and tried to compile the sources with qmake and make.. his code hates my machine! So i will have to wait for a better binary release.

Better luck to you!

---

### Post by jcmorales85 on 2007-09-07
When I insert this in my terminal:

libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb7efd000)
libQtXml.so.4 => /usr/lib/qt4/libQtXml.so.4 (0xb7ebd000)
libQtGui.so.4 => /usr/lib/qt4/libQtGui.so.4 (0xb784f000)
libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7805000)
libX11.so.6 => /usr/lib/libX11.so.6 (0xb7669000)
libQtNetwork.so.4 => /usr/lib/qt4/libQtNetwork.so.4 (0xb7612000)
libQtCore.so.4 => /usr/lib/qt4/libQtCore.so.4 (0xb74a6000)
libstdc++.so.6 => /usr/lib/gcc/i686-pc-linux-gnu/4.1.1/libstdc++.so.6 (0xb73a0000)
libm.so.6 => /lib/libm.so.6 (0xb737c000)
libgcc_s.so.1 => /usr/lib/gcc/i686-pc-linux-gnu/4.1.1/libgcc_s.so.1 (0xb7372000)
libc.so.6 => /lib/libc.so.6 (0xb7251000)
/lib/ld-linux.so.2 (0xb7f1e000)

I get this:

[http://img178.imageshack.us/my.php?image=screenshotjcmorales85woaz0.png](http://img178.imageshack.us/my.php?image=screenshotjcmorales85woaz0.png)

I've installed qmake but have never used it, I'm trying to figure it out.

---

