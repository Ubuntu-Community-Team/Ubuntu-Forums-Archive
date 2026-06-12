---
title: "How to customize live cd image on first menu, and usplash."
date: 2009-09-02
forum: Development CD/DVD Image Testing
---

### Post by The_Phantom on 2009-09-02
Hi! I'm working on a custom live cd of ubuntu 8.04-3 ... I terminate the functionally customization, now I'm working on a graphical customization and I have problem with some details.

I need help for a graphical customization of the grub and usplash. 

How to change the top image with ubuntu logo in the first menù shown by live cd in wich you can choose the running options?

Subsequently, how to change the usplash image?

Tnks to anyone will reply to that questions.

---

### Post by matsuzine on 2009-09-04
Have you considered using Reconstructor to help with the rebranding of Ubuntu?  It's very easy to use.

If you want to do it the old fashioned way, this might help:

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
[http://news.softpedia.com/news/Change-Ubuntu-Bootsplash-Theme-55237.shtml](http://news.softpedia.com/news/Change-Ubuntu-Bootsplash-Theme-55237.shtml)

---

### Post by The_Phantom on 2009-09-07
No, remastersys, reconstructor and other similar tools don't work for my customization... I need to do manual customization, because i need to use my particoular kernel, i tried with some customization tool and no one works for this. My custom live cd work only if i customize it by manual way.

I solved the problem of starting menu, now i need help for usplash. 

How to customize usplash in live cd?? I need my usplash when the system boot from cd.

Previous link don't solve my problem.

---

### Post by odeconmum on 2009-10-27
Glad to hear you're using this: I plan to keep it much more aggressively up-to-date than has been the case in the past, but don't hesitate to let me know if you find errors or need clarifications.:D

---

### Post by bodhi.zazen on 2009-10-30
It is neither easy or hard :

[http://mundomagic.org/content/usplash-install-themes-and-customize-boot-ubuntu](http://mundomagic.org/content/usplash-install-themes-and-customize-boot-ubuntu)

[http://news.softpedia.com/news/Change-Ubuntu-Bootsplash-Theme-55237.shtml](http://news.softpedia.com/news/Change-Ubuntu-Bootsplash-Theme-55237.shtml)

Other then startupmanager I have not seen a way to set the usplash image (must be a way, I just do not know it).

---

### Post by scradock on 2009-11-07
> **bodhi.zazen said:**
> It is neither easy or hard :

[http://mundomagic.org/content/usplash-install-themes-and-customize-boot-ubuntu](http://mundomagic.org/content/usplash-install-themes-and-customize-boot-ubuntu)

[http://news.softpedia.com/news/Change-Ubuntu-Bootsplash-Theme-55237.shtml](http://news.softpedia.com/news/Change-Ubuntu-Bootsplash-Theme-55237.shtml)

Other then startupmanager I have not seen a way to set the usplash image (must be a way, I just do not know it).
Unfortunately the first link leads to an instruction set with multiple errors: the line

sudo update-alternatives - config-usplash artwork.so     contains at least three.

Since linux command line expects exactly correct strings, this is unhelpful.

In this instance, it is neither easy nor difficult, but impossible to make the changes asked for using these instructions.

The correct line should be:

sudo update-alternatives --config usplash-artwork.so

HTH

---

