---
title: "gloobus preview: libpoppler missing"
date: 2011-05-01
forum: Desktop Environments
---

### Post by xtracool_protik on 2011-05-01
Hi everyone,
 Yesterday I upgraded to 11.04 and I'm liking it a lot :) (will take some time to get used to unity one though), I'm loving Byobu terminal in particular.

 Anyways apart from that I started using nautilus-elementary over nautilus it is pretty good :) to get things prettier I tried installing gloobus preview and got stuck:

 ```
The following packages have unmet dependencies:
 gloobus-preview : Depends: libpoppler7 but it is not installable
E: Broken packages

```

I've libpoppler and libpoppler-dev installed

Any ideas?

---

### Post by captainkibble on 2011-05-01
Same problem here. Bug report has already been submitted by someone: [https://bugs.launchpad.net/gloobus-preview/+bug/774270](https://bugs.launchpad.net/gloobus-preview/+bug/774270)

Tried to compile from source but ./autogen.sh craps out looking for swfdec-0.8, which isn't available in Natty. Compiling that craps out with missing alsa, which has been replaced with alsa-base. I've spent a bit of time trying to get gloobus-preview to compile without swfdec but with no joy. I have now hit my dicking around limit.

Anyone else had any joy getting gloobus-preview to work on Natty?

---

### Post by xtracool_protik on 2011-05-01
I guess we will have to wait till bug fix then :(

Anyways until then here is what I did:
 Downloaded libpoppler7 from here: [http://pkgs.org/ubuntu-10.10/ubuntu-updates-main-amd64/libpoppler7_0.14.3-0ubuntu1.2_amd64.deb.html](http://pkgs.org/ubuntu-10.10/ubuntu-updates-main-amd64/libpoppler7_0.14.3-0ubuntu1.2_amd64.deb.html)

 installed it but then gloobus preview gives errors post installation: 
 > /var/lib/dpkg/info/gloobus-preview.postinst: 33: gdk-pixbuf-query-loaders: not found

 Just installed > sudo apt-get install cutter-gtk-support

 then again installed gloobus preview and voila I've gloobus preview :D

ALTERNATIVE solution:
 I didn't try this one but possibly we can put symlink for libpoppler13 saying its libpoppler7 and try installing gloobus preview (I didn't follow it if anyone can please update me)

 I've attached screenshot for one of my paintings :P

---

### Post by captainkibble on 2011-05-01
Your suggestion of installing libpoppler7 from 10.10 worked for me too. Not the optimum solution but it will do until an update comes along. 

Thanks for that. =D>

---

### Post by xtracool_protik on 2011-05-01
> Your suggestion of installing libpoppler7 from 10.10 worked for me too. Not the optimum solution but it will do until an update comes along.

Thanks for that. 

Glad it helped :D

---

### Post by aldais on 2011-05-08
guys,

I think you all might want to hear about this.
Apparently, today, the dependencies of gloobus-preview package was changed to libpoppler13 which is found in natty, instead of the old libpoppler7 from maverick. so it's safe to remove the library from maverick now.

---

### Post by xtracool_protik on 2011-05-08
> guys,

I think you all might want to hear about this.
Apparently, today, the dependencies of gloobus-preview package was changed to libpoppler13 which is found in natty, instead of the old libpoppler7 from maverick. so it's safe to remove the library from maverick now.

Thanks for the tip its working even after complete removal of libpoppler7 which upgraded gloobus-preview by itself :)

---

