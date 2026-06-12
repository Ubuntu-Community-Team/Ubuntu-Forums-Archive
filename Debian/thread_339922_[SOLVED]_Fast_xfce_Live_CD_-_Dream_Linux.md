---
title: "[SOLVED] Fast xfce Live CD - Dream Linux"
date: 2007-01-16
forum: Debian
---

### Post by victorbrca on 2007-01-16
Hi all,


  Just got my hands on 2x Linux live CD distros from Brazil. One of them runs on xfce and is amazingly fast.

  I have no real experience with Live CDs that run of xfce, but I was amazed with the speed... (and so were my co-workers that do not like Linux)

- Dream Linux
  . Site: [http://dreamlinux.com.br/](http://dreamlinux.com.br/)
  . Runs on xfce (or gnome or KDE)
  . Very fast
  . English and Portuguese

- Kalango Linux
  . Site: [http://www.kalangolinux.org/](http://www.kalangolinux.org/)
  . Runs on KDE and gnome
  . Considerably fast for gnome
  . Portuguese only :(


Vic.

---

### Post by RAV TUX on 2007-01-16
moving to the Debian forum

---

### Post by victorbrca on 2007-01-17
> **RAV TUX said:**
> moving to the Debian forum

Sorry!!!!    :-?

---

### Post by fuscia on 2007-01-20
i was too busy noticing how pretty it is to notice how fast it is.

---

### Post by victorbrca on 2007-01-20
> **fuscia said:**
> i was too busy noticing how pretty it is to notice how fast it is.

Is it faster than Xubuntu live CD?

---

### Post by AgenT on 2007-01-21
Here is another distribution that may be of interest (from Argentina):
[https://www.ututo.org/www/](https://www.ututo.org/www/)

Richard Stallman [uses this distribution]("http://www.stallman.org/stallman-computing.html") on his computer.

---

### Post by victorbrca on 2007-01-21
> **AgenT said:**
> Here is another distribution that may be of interest (from Argentina):
[https://www.ututo.org/www/](https://www.ututo.org/www/)

Richard Stallman [uses this distribution]("http://www.stallman.org/stallman-computing.html") on his computer.

I'll give it a try!!! Thanks!!!

> **victorbrca said:**
> Is it faster than Xubuntu live CD?

I tried Xubuntu live cd and it's pretty fast as well.

But I think DreamLinux is very elegant (has a MAC OS look) and seemed faster than Xubuntu....

[[img]http://dreamlinux.incubadora.fapesp.br/portal/arquivos/mini-desktop2.jpg[/img]](http://dreamlinux.incubadora.fapesp.br/portal/arquivos/desktop.jpg)


Vic.

---

### Post by AgenT on 2007-01-21
One warning: [Engage]("http://www.enlightenment.org/Applications/Engage/"), the Enlightenment 17 launcher/docker that DreamLinux uses is not stable and has some serious issues. And it is probably even more unstable in the stand-alone version that DreamLinux uses. For example, I believe the intergrated version has drap and drop functionality (the other E17 dock does).

Here is the much better [documentation on Engage]("http://www4.get-e.org/EFL_User_Guide/English/_pages/3.4.html") and it's status.

But DreamLinux does look attractive from a "ready to use" stand point. Do note that you can get that same setup using Debian (it could be more difficult with Ubuntu because some of the programs, like Engage, are not up-to-date on Ubuntu in any known repository). You would have to install XFCE4, Engage and some of the other applications that you want (Inkscape, etc.).

One other thing worth noting: DreamLinux is based on Debian and Morphix, which looks as if Morphix is itself based on Debian. Hopefully DreamLinux does not try to mix and match packages from both as that could cause major upgrade problems in the future.

UPDATE: DreamLinux website mentions that it uses fully open source software. However, this is not true. They use XaraLX which is not fully open source - only the GUI is, but not the main core (or library as it is called). Their website is deceiving and you have to dig around to find this out. I myself thought it was open source at first as well. Hopefully someone tells the DreamLinux folks because it may not be legal for them to distribute it in a distro as they are now.

---

### Post by victorbrca on 2007-01-27
> **AgenT said:**
> One warning: [Engage]("http://www.enlightenment.org/Applications/Engage/"), the Enlightenment 17 launcher/docker that DreamLinux uses is not stable and has some serious issues. And it is probably even more unstable in the stand-alone version that DreamLinux uses. For example, I believe the intergrated version has drap and drop functionality (the other E17 dock does).

Here is the much better [documentation on Engage]("http://www4.get-e.org/EFL_User_Guide/English/_pages/3.4.html") and it's status.

But DreamLinux does look attractive from a "ready to use" stand point. Do note that you can get that same setup using Debian (it could be more difficult with Ubuntu because some of the programs, like Engage, are not up-to-date on Ubuntu in any known repository). You would have to install XFCE4, Engage and some of the other applications that you want (Inkscape, etc.).

One other thing worth noting: DreamLinux is based on Debian and Morphix, which looks as if Morphix is itself based on Debian. Hopefully DreamLinux does not try to mix and match packages from both as that could cause major upgrade problems in the future.

UPDATE: DreamLinux website mentions that it uses fully open source software. However, this is not true. They use XaraLX which is not fully open source - only the GUI is, but not the main core (or library as it is called). Their website is deceiving and you have to dig around to find this out. I myself thought it was open source at first as well. Hopefully someone tells the DreamLinux folks because it may not be legal for them to distribute it in a distro as they are now.


Should I take them that DreamLinux sucks and it's illegal??


Vic.

---

### Post by AgenT on 2007-01-27
> **victorbrca said:**
> Should I take them that DreamLinux sucks and it's illegal??Whether or not it "sucks" is up to you. Do note that the DreamLinux developers may not be aware of the problem because Xara people try to confuse everyone and make it look like it is 100% freedom  software. 

XaraLX is *NOT* freedom software and actually has a restrictive license as well as a GPL license.  Granted, the GUI is open source and under the GPL, but not the library which is the most important and all the GPL code without the library is pretty much useless. This is why no one has signed up to help them develop it.

The library in question is not open source but a pre-compiled binary and is tied to the program and must be included with the program. This library is not open or free as in freedom and has a [restrictive license]("http://svn.xara.com/?do=view&project=XaraLX&path=/Trunk/XaraLX/libs/LIBS-LICENSE").

What the legal ramifications of this should be left to a FSF lawyer but my guess would be that according to the restrictive license, distributing XaraLX in a distribution is allowed. But then again, it may be infringing on the GPL'ed code of not only XaraLX but the countless other packages included in the distribution.

Please also note that whatever applies to DreamLinux also applies to Ubuntu because Ubuntu also has [XaraLX in its repositories]("http://packages.ubuntu.com/edgy/graphics/xaralx").

---

