---
title: "Input methods can't be activated in Abobe AIR"
date: 2010-10-18
forum: Desktop Environments
---

### Post by m_yanagisawa on 2010-10-18
Hi! I'm using Ubuntu 10.10 amd64 desktop in Japanese.

Adobe AIR is not officially supported, but I've installed ia32-libs
and downloaded "AdobeAIRInstaller.bin" from Adobe's site, applied it.
After that I can use some AIR applications.

But when I tried to type Japanese into AIR application (such as TweetDeck),
input method "ibus" cannot be activated.

I usually use anthy-ibus, but situation is not changed when I used scim
(anthy-scim).

What should I do to activate IM in AIR? 


My environment variables are now like this.

$ echo $LANG
ja_JP.utf8

$ echo $LANGUAGE
ja_JP:ja:en_GB:en

$ echo $QT_IM_MODULE
ibus

---

