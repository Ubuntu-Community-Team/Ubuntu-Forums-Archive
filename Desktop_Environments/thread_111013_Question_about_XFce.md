---
title: "Question about XFce"
date: 2006-01-01
forum: Desktop Environments
---

### Post by Sophisto on 2006-01-01
Hi! Have been reading about Xubuntu and since I just came over a P3 750 laptop I thought this could be an interesting alternative to use on such computer. Did not however find a section for Xubuntu and thats the reason for posting here. 

My question might be a bit silly but I know that with GNOME one can easily use KDE supported software like amaroK. Is this the same with Xfce? I.e that one can simply apt-get install Gnome/KDE software as one may like? If this would be the case wouldnt that defeat the whole purpopse of such desktop environment like xfce (lightweight etc.)? 

Thanks a lot!

---

### Post by az on 2006-01-01
[QUOTE=Sophisto]a P3 750 laptop I thought this could be an interesting alternative to use on such computer.  [/QUOTE]

You can happily run the default install on a PII 400 MHz.  If you pave a pentium 750Mhz, there is no need to use a lightweight desktop at all.


[QUOTE=Sophisto]
My question might be a bit silly but I know that with GNOME one can easily use KDE supported software like amaroK. Is this the same with Xfce? I.e that one can simply apt-get install Gnome/KDE software as one may like? If this would be the case wouldnt that defeat the whole purpopse of such desktop environment like xfce (lightweight etc.)? 

Thanks a lot![/QUOTE]


That's not a silly question.  Unix uses shared libraries (just like other operating systems)  A lightweight desktop environment just does not use really heavy libraries by default.  That does not stop you from using other apps which use more ressource-hungry libraries, but you will have to wait for those libraries to load when you run that app.

So if you have only a small amount of memory, for example, everything will run fine until you start a big KDE application.  The KDE libraries will load and occupy a lot of memory.  Your system will slow down while you are running that app.

A lightweight desktop just leaves you more room to run other apps.  It does not change the way other applications use memory and processor cycles.

---

### Post by Sophisto on 2006-01-03
Thanks for your reply. I know that I could use Ubuntu on my laptop but its just that I would like to have a really fast desktop environmnent.

My last question; so the libraries one loads for e.g. amaroK would not continue to occupy memory once it has been shut down?

---

