---
title: "Firefox problem with ad banners and webpage menus"
date: 2009-01-18
forum: General Help
---

### Post by brunolabs on 2009-01-18
Hi!

I use Firefox 3.0.5.
I have a problem viewing webpages which have drop-down menus (like the ones here in ubuntu forums) and have imediately below them ad banners. The banners completely cover the menu and makes it impossible to view and/or click the options.

Is there a way to solve the problem? Or maybe a way to put the drop-down menus in front of the ads?

Thanks!

---

### Post by binbash on 2009-01-18
can you please post a screenshot?I do not think this is a firefox issue

---

### Post by DeMus on 2009-01-18
> **brunolabs said:**
> Hi!

I use Firefox 3.0.5.
I have a problem viewing webpages which have drop-down menus (like the ones here in ubuntu forums) and have imediately below them ad banners. The banners completely cover the menu and makes it impossible to view and/or click the options.

Is there a way to solve the problem? Or maybe a way to put the drop-down menus in front of the ads?

Thanks!

I do know what you mean. I had it sometimes on the msn.com website where you can watch a video, but the little screen was all covered by an ad. At the moment I don't have it and I have no idea what caused it or what I did to fix it. It just disappeared "by itself".

---

### Post by lswb on 2009-01-18
This was a problem with some sites using flash for ads and animations in older versions of the adobe flash plugin for firefox. From your firefox menu, select Tools/Addons/Plugins and scroll down to the "Shockwave Flash" entry. The version shoud be "10.0 r12" for the 32 bit flash plugin. (I'm not sure what the recently released 64 bit plugin shows)

If you are running an older version try installing the latest from synaptic. Search for the package name "flashplugin-nonfree" Adobe now has a .deb package availble from their website also.

It is not unusual to have problems with flash installation so if firefox doesn't start using the new version after installation, search the forums/google for solutions or start a new thread with details.

---

### Post by brunolabs on 2009-01-18
Thanks!!!

That was the problem. I was running version 9. Downloaded the new version from the Adobe site (the one on the Package Manager was outdated as well).

It works correctly now.

Thanks again. :)

---

### Post by brandon4256 on 2009-04-05
I still have this problem too. I've installed the latest flash plugin from adobe and it fixes it until firefox tells me I need to update my flash plugin then it proceeds to make me download the "non-free plugin".

what am i doing wrong?

---

