---
title: "Distro upgrade has messed up display... and more"
date: 2010-10-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mrodent on 2010-10-07
Dear all,

VERY ANNOYED NEWBIE ALERT.

A few weeks ago after much tearing of hair and other appendages I finally succeeded in installing 10.10 (64 bit beta) on my E6410.  All prior attempts had failed utterly because, seemingly, previous versions couldn't cope with the graphics card ("Intel HD Graphics" - why can't Dell be more specific?  Someone else said "often referred to as Intel GMA 500 (or Poulsbo)").

I have just suffered a distro upgrade which had left my display in a fragile state: icons and such are getting "broken up".  It's usable ... but this situation is HIGHLY ANNOYING.  The quality of the screen you have in front of you is ABSOLUTELY CRITICAL for doing anything on your computer.  If things worked OK with the 10.10 beta, why couldn't the Ubuntu developers make sure this new distro upgrade worked Ok with this oddly nameless Intel GPU?  (... but used in a Dell machine, so not that obscure, guys).

Fortunately I am still just messing with Ubuntu in a dual boot arrangement.  NB the distro upgrade also played with my grub boot file (changing the default OS to boot to.  It SHOULDN'T DO THIS).

Fortunately too I have taken a Macrium image of the Linux partition after the successful install... I have three questions now
1) how do I STOP, PREVENT AND PROHIBIT future distro upgrades completely?
2) how do I configure future distro upgrades so they don't mess with the graphics settings?  (or "roll back" if this is possible)
3) how do the Ubuntu authorities, whoever they are, get told about this?  With a view, maybe, to supplying some sort of driver for what is obviously a highly problematic GPU?

Thanks

---

### Post by mörgæs on 2010-10-07
GMA 500 is a well-known problem. You can be assured that it is also known in the developer circles.

In 'software sources' you can choose not to be informed of dist-upgrades. If some day you want to upgrade, which is not necessary in the near future since 10.04 is supported for three years, go for a clean install.

---

### Post by mrodent on 2010-10-08
Thanks... you've said just want I wanted to hear and told me what I want to know!

---

