---
title: "synaptic package manager wont install imagemagick"
date: 2006-03-20
forum: Desktop Environments
---

### Post by Finster101 on 2006-03-20
Hi,

I am new to ubuntu (using 5.10 btw) and the synaptic package manager.  I was able to install many of the utils/apps/games that I wanted to add to my system with the synaptic package manager but it gives me an error when I try to add imagemagick.  Here is the error:

imagemagick:
  Depends: libmagick6 (=6:6.2.3.4-1ubuntu1) but 6:6.2.3.4-1ubuntu1.1 is to be installed

I can't seem to find the library it wants or how to overide this and just do it (Would that even work?)

Where do I go from here?
Thanks in advance

---

### Post by TwistedLogic on 2006-03-20
Hi,

In synaptick package manager search for libmagick6, and  post the search results, that is what versions are installed and what is the latest version available. 

I believe you already have a diffrent version of libmagick installed on your system which is conflicting with the imagemagick installation. If you remove libmagick and then again try installing imagemagick the installation should work.

:-D

---

### Post by Finster101 on 2006-03-20
That did the trick, thanks! :mrgreen:

---

