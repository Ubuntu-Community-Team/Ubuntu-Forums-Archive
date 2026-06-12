---
title: "Wifi-radar in KDE"
date: 2005-08-30
forum: Desktop Environments
---

### Post by daller on 2005-08-30
Hi All,

I just installed wifi-radar - and it works better than kwifimanager (does kwifimanager work at all?)

My question is how to get wifi-radar minimize to the systray!

Is there a KDE alternative?

---

### Post by drizek on 2005-08-30
[QUOTE=daller]Hi All,

I just installed wifi-radar - and it works better than kwifimanager (does kwifimanager work at all?)

My question is how to get wifi-radar minimize to the systray!

Is there a KDE alternative?[/QUOTE]
 there is a cool KDE wifi app on kde-apps.org

kde apps is down ATM though, so you will have to just check back tomorrow or somehting. i dont remember what it was called, but it was updated recently, so it should be on the first couple pages.

---

### Post by daller on 2005-08-30
This one?

[http://kde-apps.org/content/show.php?content=21832](http://kde-apps.org/content/show.php?content=21832)

Downloaded the source, and ran "sudo sh configure"

after a while, it exits with an error:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

What can I do about that?

---

### Post by drizek on 2005-08-30
ya, thats it.  try the debian package here [http://wlassistant.sourceforge.net/](http://wlassistant.sourceforge.net/)

---

### Post by daller on 2005-08-31
Well, I would like to build it from scratch!

Using debian-package on ubuntu may have the system crash!

Please help me run "sh configure"!

---

### Post by daller on 2005-08-31
I also have to overcome this:

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

vi /lib/cpp - looks like shit! - Think its binary!

---

### Post by drizek on 2005-08-31
[QUOTE=daller]Well, I would like to build it from scratch!

Using debian-package on ubuntu may have the system crash!

Please help me run "sh configure"![/QUOTE]
 it wont break anything if you use the debian one. even if it doesnt work, you just need to do apt-get remove whatever and it gets rid of it and your system goes back to the way it was before.

if you insist on compiling it by hand however, then go into synaptic and search for the name(not description)

x.org

then look for packages that have "-devel" at the end and install those. installing hte devel packages should fix your compile problem. but its a lot easier to use the debian packages ;)

---

### Post by daller on 2005-08-31
Can't use port 21, here at work, so can't use FTP...

---

### Post by daller on 2005-09-03
Trying to install it from the repo, errors this:

wlassistant: 

Depends: kdelibs4 (>= 4:3.3.2-6.1) men den kan ikke installeres
Depends: libiw27 (>= 27) men den kan ikke installeres
Depends: libqt3c102-mt (>= 3:3.3.4) men den kan ikke installeres

What can I do about that?

---

### Post by daller on 2005-09-03
I've installed it with a ubuntu-customized deb now - but how do I execute wlassistant?

---

