---
title: "Menu text missing for GTK apps like Audacity and XMMS"
date: 2006-11-18
forum: Desktop Environments
---

### Post by rvbhute on 2006-11-18
I installed Ubuntu 6.10 today and am very glad I moved from 6.06 :) It is a lot better, no matter what others say.

Two things which have improved over 6.06 are
1. locale setting no longer gives warnings.
2. A lot more applications look *smoother*.

However there are a few gripes.
1. Using apt-get update, gives me a lot of errors (tagged Ign) involving "Translation en_IN:en". IN, coincidently, is my locale, India.
2. Firefox 2 crashes if I install the flashplayer plugin.

And most importantly, applications like Audacity and XMMS are missing their menu texts. If I click on the place where the menu is supposed to be, I get the menu drop down with the shortcuts visible, but no text! 
e.g. I see "Ctrl+Z" but no text beside it.

I'm missing some GTK libraries or something, but which I don't know. And I'm wondering how the apps got installed in the first place with missing libraries.

---

### Post by kallu_be on 2006-11-18
same with me. I think its the problem with "en_IN" locale. Attaching the screenshot.

---

### Post by rvbhute on 2006-11-19
System > Administration > Language Support 

I set the language to English (United States of America) instead of English (India) and the problem got solved.

---

### Post by almostlinux on 2006-11-19
> **rvbhute said:**
> System > Administration > Language Support 

I set the language to English (United States of America) instead of English (India) and the problem got solved.

This should probably be reported as a bug.

---

