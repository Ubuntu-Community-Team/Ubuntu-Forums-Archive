---
title: "Open Office 2.0 beta, Firefox 1.04?"
date: 2005-06-14
forum: Desktop Environments
---

### Post by orev on 2005-06-14
Are these working for anyone on Kubuntu 5.04?

I have updated my repositories, I don't seem to be able to apt-get either.  Maybe I am just using the wrong method or package name?

Can anyone point me to a url, or line me up with some information on this?

OO 2.0 is quite a bit better than previous versions in my opinion (been running it Winstyle), and the Firefox website won't let me download extentions until I upgrade Firefox.

Help please?

---

### Post by philipacamaniac on 2005-06-14
The Firefox package is updated, it just doesn't have the correct version number. See bug [https://bugzilla.ubuntu.com/show_bug.cgi?id=10681](https://bugzilla.ubuntu.com/show_bug.cgi?id=10681) and see comment 3 for the fix.

There is openoffice.org2 in the Universe repository. Reply if you need help enabling Universe.

---

### Post by orev on 2005-06-14
I have the universe respository updated.

can I apt-get openoffice.org2?  If so, what is the correct package? ie.  sudo apt-get __________________  ?

Your kindness will be repaid.... :)

---

### Post by elsewhere on 2005-06-14
Try apt-get openoffice.org2, that's the meta-package that should pull down the main packages.  Since this is the Kubuntu forum, I'll assume you're running KDE and recommend you pull down openoffice.org2-kde as well, for KDE-integration.

There's also a HOWTO elsewhere on this board for creating more current ooo2 packages for k/ubuntu, the ones in the repository are an older version of the beta, but they work well enough for me and were painless to install.

Hope this helps...

Cheers,
KV

---

### Post by orev on 2005-06-14
Thanks.

Someone else posted the individual packages on another thread:

[http://ubuntuforums.org/showthread.php?t=41720](http://ubuntuforums.org/showthread.php?t=41720)

I tried apt-get openoffice.org2 and that did not seem to work.  Terminal says its an invalid operation.

I am running the KDE.

THANKS!

---

### Post by orev on 2005-06-14
sorted it out through synaptic....

thank you...

---

### Post by SanderAnt on 2005-06-14
For what it's worth, the build that's in universe is quite old, and the spellchecker doesn't work which is a deel breaker for me.  :-P

---

### Post by philipacamaniac on 2005-06-16
[QUOTE=SanderAnt]For what it's worth, the build that's in universe is quite old, and the spellchecker doesn't work which is a deel breaker for me.  :-P[/QUOTE]

Spell check doesn't work without the spell check engine. You have to install myspell-en (why it doesn't get installed automatically - that's beyond my understanding).

---

