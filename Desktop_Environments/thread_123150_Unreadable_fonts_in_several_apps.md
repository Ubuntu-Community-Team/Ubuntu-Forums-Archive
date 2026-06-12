---
title: "Unreadable fonts in several apps"
date: 2006-01-29
forum: Desktop Environments
---

### Post by theFallen on 2006-01-29
Hi all,

I have a strange Problem. As for Firefox I got it solved by installing a new version, but Eklipse and aMule are still not working properly.
It is not possible to read some lines, the fonts are all scrambled, but when I mark them I can read them most of the times, until I undo the marking.
I have transparancy enabled, but again after disabling it and uncommenting the needed part in xorg.conf (and a reboot) it still does not work.
And when I check kde to use its own colors for not kde apps, some apps crashes.

---

### Post by obibok on 2006-01-29
Not sure if this will help but you could try installing more fonts just in case the apps you use have problems handling your current set. Besides, the default font selection in Ubuntu is rather... incomplete :-#

Try:
```
# sudo apt-get install ttf-bitstream-vera ttf-dejavu ttf-dustin ttf-f500 ttf-freefont ttf-gentium ttf-isabella ttf-junicode ttf-larabie-deco ttf-larabie-straight ttf-larabie-uncommon ttf-mgopen ttf-opensymbol ttf-staypuft ttf-summersby ttf-thryomanes ttf-ubuntu-title ttf-xfree86-nonfree
```

I had a problem with *Krita* making some fonts too tiny, so I had to force a  minimum font size 7 pt in *.fonts.conf*.

---

### Post by Glauco on 2006-01-30
Try *dpkg-reconfigure fontconfig* in a console session. Choose *autohinter* option.

---

### Post by theFallen on 2006-02-06
Hi thanks for your hints, but it didn't work :(
I did an update of sun's java, but that didn't do the trick either.
It seems only to happen in java applications.
Do I have to do a restart after reconfiguring the fonst? 
Yes, I did restart the application :D

---

### Post by theFallen on 2006-02-22
Has no one the same problem?
It seems to be a rendering problem of a font.
I'm quite certain now that it only happens to Java applications.
Can Java in generall be configured so to use certain fonts?
What are those fonts in xorg.conf? Which of those are necessary?

---

