---
title: "quick fix: PDF plugin for claws-mail (3.5+) on Intrepid"
date: 2009-01-19
forum: Desktop Environments
---

### Post by owczi on 2009-01-19
Hi everyone,

Thought somebody might find this useful: Claws Mail team have dropped the PDF viewer plugin in 3.5 from it's official plugin collection because of licensing issues - yet this plugin was the one I used most. It turns out that the plugin from the last release where it was included (3.4) builds fine on both Hardy and Intrepid (as long as you ave all relevant -dev packages installed) and works wich claws-mail 3.5+. If anyone wants to get this running - either download claws-mail-extra-plugins-3.4.1 from sourceforge (./configure in the pdf_viewer subdirectory will nicely point out missing dependencies), or if you happen to be running Intrepid on i386 - use attached file (build for claws-mail 3.7.0, place it in /usr/lib/claws-mail/plugins). Unfortunately I have no time to build a .deb for this, but guess that's enough just to get the pdf viewer working.

regards,
owczi

---

### Post by gborzi on 2009-02-19
> **owczi said:**
> Hi everyone,

Thought somebody might find this useful: Claws Mail team have dropped the PDF viewer plugin in 3.5 from it's official plugin collection because of licensing issues - yet this plugin was the one I used most. It turns out that the plugin from the last release where it was included (3.4) builds fine on both Hardy and Intrepid (as long as you ave all relevant -dev packages installed) and works wich claws-mail 3.5+. If anyone wants to get this running - either download claws-mail-extra-plugins-3.4.1 from sourceforge (./configure in the pdf_viewer subdirectory will nicely point out missing dependencies), or if you happen to be running Intrepid on i386 - use attached file (build for claws-mail 3.7.0, place it in /usr/lib/claws-mail/plugins). Unfortunately I have no time to build a .deb for this, but guess that's enough just to get the pdf viewer working.

regards,
owczi

Hello Owczi,
while searching for the pdf viewer in intrepid, I found your post, but having x86_64 installed and some free time I made a package for claws-mail-pdf-viewer. It is attached to this post along with the .diff file, in case you want to build it for i386.
I have used the hardy package to make this one.

Regards.

---

### Post by Hemanti on 2009-04-07
Thank you. Having at last managed to compile, it works like a charm. ;)

---

### Post by dominik.holler on 2009-10-23
build on 8.04.3 hardy against claws-mail 3.7.3-1hardyubuntu3 from ppa:
```
sudo aptitude install libpoppler-dev libpoppler-glib-dev libenchant-dev libclaws-mail-dev
wget [http://aur.archlinux.org/packages/claws-pdf-viewer/claws-pdf-viewer/pdf_viewer-0.9.3.tar.gz](http://aur.archlinux.org/packages/claws-pdf-viewer/claws-pdf-viewer/pdf_viewer-0.9.3.tar.gz)
tar xvzf pdf_viewer-0.9.3.tar.gz 
cd pdf_viewer/
./configure
make
find . -name pdf_viewer.so
sudo mv ./src/.libs/pdf_viewer.so /usr/lib/claws-mail/plugins/
```

---

### Post by dominik.holler on 2011-03-14
Version  0.9.4-1 of archlinux.org is still working
```

 wget http://aur.archlinux.org/packages/claws-pdf-viewer/claws-pdf-viewer.tar.gz
...
aclocal
touch ./ABOUT-NLS
automake
./configure 
make
find . -name pdf_viewer.so 
sudo mv ./src/.libs/pdf_viewer.so /usr/lib/claws-mail/plugins/

```

---

### Post by alzurzin on 2012-06-04
has anyone a source for a current version of pdf-viewer for Claws 3.8 running on Ubuntu 12.04 ?

---

