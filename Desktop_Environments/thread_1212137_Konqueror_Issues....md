---
title: "Konqueror Issues..."
date: 2009-07-13
forum: Desktop Environments
---

### Post by izizzle on 2009-07-13
I recently switched over from Firefox to Konqueror because for me, Konqueror is faster and fits right into the KDE desktop. I do have some problems though. First of all, flash. On some sites flash will work, but on others it won't. ([WORKS]("http://www.adobe.com/software/flash/about/")) ([DOESN'T WORK]("http://www.southparkstudios.com/episodes/220764/")) Second, java. When a site tries to access Java, the applet loads, but it does not work at all.

I'm running Kubuntu 64-Bit. Any ideas?

Thanks.

---

### Post by aged hippy on 2009-07-13
You probably need ***adobe-flashplugin, swfdec-mozilla,** *and ***flashplugin-nonfree*** from the repos.

---

### Post by SuperSonic4 on 2009-07-13
> **aged hippy said:**
> You probably need ***adobe-flashplugin, swfdec-mozilla,** *and ***flashplugin-nonfree*** from the repos.

Why would a mozilla plugin work in konqueror?

I cannot be sure because adobe's flash works with mine nor can I access the South Park site (because of country restrictions). Youtube works though

It could just be the site? Adobe's 64 bit plugin should work but I can't remember where it goes in konqueror >.< - my konqueror does refer to ~/.mozilla/plugins though as well as others

---

### Post by aged hippy on 2009-07-13
> **SuperSonic4 said:**
> Why would a mozilla plugin work in konqueror?


... ummm... i'll put my glasses on. :oops:

:)

---

### Post by izizzle on 2009-07-13
No such thing as adobe-flashplugin and the other two you listed are already installed. Konqueror lists the plugins and plays flash on some sites but on some sites it does not. I know it's not an issue with the site because it works in Firefox!

---

### Post by izizzle on 2009-07-13
I ran Konqueror from the terminal. I started up google, went to the southpark site, and tried to play the video then shut it down. Here is the output:

```
QPainter::begin: Widget painting can only begin as a result of a paintEvent                                             
QPainter::translate: Painter not active                     
QPainter::setClipRect: Painter not active                   
QPainter::hasClipping: Painter not active                   
QPainter::setPen: Painter not active                        
QPainter::setBrush: Painter not active                      
QPainter::drawRects: Painter not active                     
QPainter::font: Painter not active                          
QPainter::setFont: Painter not active                       
QPainter::font: Painter not active                          
QPainter::setFont: Painter not active                       
QPainter::setPen: Painter not active                        
QPainter::hasClipping: Painter not active
QPainter::setPen: Painter not active
QPainter::setBrush: Painter not active
QPainter::drawRects: Painter not active
QPainter::hasClipping: Painter not active
QPainter::setPen: Painter not active
QPainter::setBrush: Painter not active
QPainter::drawRects: Painter not active
QPainter::hasClipping: Painter not active
<unknown program name>(4389)/ main: 2 - parseCommandLine
<unknown program name>(4389)/ main: 3 - create KApplication
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4401): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64
QPainter::begin: Widget painting can only begin as a result of a paintEvent
QPainter::translate: Painter not active
QPainter::setClipRect: Painter not active
QPainter::hasClipping: Painter not active
QPainter::hasClipping: Painter not active
QPainter::hasClipping: Painter not active
QPainter::hasClipping: Painter not active
QPainter::hasClipping: Painter not active
QPainter::hasClipping: Painter not active
QPainter::hasClipping: Painter not active
QProcess: Destroyed while process is still running.
```

It gave an error about some canberra library. Any ideas?

---

### Post by izizzle on 2009-07-14
Bump. Anyone?

---

