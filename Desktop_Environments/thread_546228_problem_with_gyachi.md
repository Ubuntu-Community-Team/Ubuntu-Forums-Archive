---
title: "problem with gyachi"
date: 2007-09-08
forum: Desktop Environments
---

### Post by tropcky on 2007-09-08
i have a problem with the gyachi  that when i try to install it its gives an error msg :
error  : dependency is not satisfiable : libgail17
plez help 
 thank u

---

### Post by tropcky on 2007-09-08
help plez

---

### Post by scxtt on 2007-09-08
what version of ubuntu are you using?  looks like edgy/feisty use v18 - is that version installed on your system?:
```
:> aptitude search gail
i   libgail-common                                    - GNOME Accessibility Implementation Library -- common module
p   libgail-dbg                                       - Gail libraries and debugging symbols
p   libgail-dev                                       - GNOME Accessibility Implementation Library -- development f
p   libgail-doc                                       - documentation files of the Gail library
p   libgail-gnome-dbg                                 - libgail-gnome library and debugging symbols
p   libgail-gnome-dev                                 - Development files of libgail-gnome
i   libgail-gnome-module                              - GNOME Accessibility Implementation Module for GnomeUI/Bonob
[color=red]i   libgail18                                         - GNOME Accessibility Implementation Library -- shared librar[/color]
```

---

### Post by tropcky on 2007-09-08
tropcky@tropcky-linux:~$ aptitude search gail
i   libgail-common                  - GNOME Accessibility Implementation Library
p   libgail-dbg                     - Gail libraries and debugging symbols      
p   libgail-dev                     - GNOME Accessibility Implementation Library
p   libgail-doc                     - documentation files of the Gail library   
p   libgail-gnome-dbg               - libgail-gnome library and debugging symbol
p   libgail-gnome-dev               - Development files of libgail-gnome        
i   libgail-gnome-module            - GNOME Accessibility Implementation Module 
i   libgail18                       - GNOME Accessibility Implementation Library
 

i use 7.4
i hop if thats helps

---

### Post by scxtt on 2007-09-08
how are you trying to install it?  *.tar.gz or *.deb?

---

### Post by tropcky on 2007-09-08
its  .deb

---

### Post by scxtt on 2007-09-08
from their [site](http://gyachi.sourceforge.net/download.shtml)?  it looks outdated ... are you using dpkg -i or Gdebi?

---

### Post by tropcky on 2007-09-08
thank u so much man its works now

---

### Post by loell on 2007-09-08
hi, so it works now?,
you might wanna know why you had that error, because in your first install you accidentally installed the dapper deb package, which will give the dependency error.

you can also use the latest CVS package 

[http://ubuntuforums.org/showthread.php?t=431290]("http://ubuntuforums.org/showthread.php?t=431290")

---

### Post by tropcky on 2007-09-08
maaaaaaaan really thanks i downloaded from the link u gived me and its work soooo god thank u so much 

with guys like u  ubuntu forums gonna be the best  forums ever

---

### Post by tropcky on 2007-09-08
i got anther problem with gyachi that i cant go 2 any chat room i chose 
i shose a chat room and i press join and i just wait and wait for ever but its not connecting 
so help plez

---

### Post by loell on 2007-09-09
did you click the captcha link? it needs to be clicked then answer the captcha page before you can enter the room.

---

### Post by tropcky on 2007-09-09
no i didnt cuz i didnt see any link

---

### Post by b30sam on 2007-09-19
I am having problems installing gyachi.
Tried the official download from source forge as well as the cvs deb both gave the error 'dependency not satisfiable libjasper-1.701-1'. I checked in Synaptic for libjasper, i got v1.9. So why this error??
I tried to compile it from source, there I got another error 
_______________________________________
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for X... no
configure: error: X development libraries not found
_______________________________________________________
Any help guys, perhaps some way to satisfy the package dependency by creating a soft link or something?

I am using Gutsy Gibbon Tribe 4

---

### Post by loell on 2007-09-19
thats because gusty had a newer jasper library, a deb package must be built from gutsy to make it installable

---

### Post by b30sam on 2007-09-20
Hmm, 
I used to be a Redhat/Fedora user, just shifted to Ubuntu. Is there any way I can build a deb package  from gutsy to make it installable.
forgive my ignorance

---

### Post by Drakeo on 2008-01-12
> **b30sam said:**
> I am having problems installing gyachi.
Tried the official download from source forge as well as the cvs deb both gave the error 'dependency not satisfiable libjasper-1.701-1'. I checked in Synaptic for libjasper, i got v1.9. So why this error??
I tried to compile it from source, there I got another error 
_______________________________________
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for X... no
configure: error: X development libraries not found
_______________________________________________________
Any help guys, perhaps some way to satisfy the package dependency by creating a soft link or something?

I am using Gutsy Gibbon Tribe 4yes gyachi looks for jasper in /usr/local/lib/pkgconfig/gyachi this tells it where to look for the libraries. and if you installed it from ubuntu it was placed in /usr/lib/pkgconfig/gyachi.. either do a sym link or install from source. Again gyachi default is /usr/local/bin/jasper thats what it looks for. make sure your jasper executable  is there.

---

### Post by Drakeo on 2008-01-12
> **Drakeo said:**
> yes gyachi looks for jasper in /usr/local/lib/pkgconfig/gyachi this tells it where to look for the libraries. and if you installed it from ubuntu it was placed in /usr/lib/pkgconfig/gyachi.. either do a sym link or install from source. Again gyachi default is /usr/local/bin/jasper thats what it looks for. make sure your jasper executable  is there.
 another problem I see is you need xorg devel installed that is where you faild

---

