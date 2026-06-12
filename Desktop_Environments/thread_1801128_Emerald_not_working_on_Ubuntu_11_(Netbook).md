---
title: "Emerald not working on Ubuntu 11 (Netbook)"
date: 2011-07-10
forum: Desktop Environments
---

### Post by underage17 on 2011-07-10
I installed a theme which requires some amount of transparency for which I needed emerald. I installed it, and installed the emerald theme in it, but when I select it, nothing happens.

I tried emerald --replace, but when I do that, the title bar in all open windows disappears
I'm running ubuntu 11 on my netbook. so far, i've been using compiz with no problem, so I don't think it's my video card's problem.

Any suggestions?

---

### Post by fullerenedream on 2011-07-10
This is the best fix I found so far, and it's disappointing. I followed the instructions and it got emerald  working. But I want to switch back and forth between emerald and metacity themes, so then I tried metacity --replace. That worked, but now emerald --replace doesn't reenable emerald for me.

Ubuntu 11.04 Fix: Enable Emerald Themes for Compiz-Fusion Window Borders (Title-Bars)
[http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/](http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/)

---

### Post by steinerd on 2011-07-10
Here is a tutorial to get emerald working on 11.04.

[http://shallows.bounceme.net/tiki-index.php?page=Enable+Emerald+Themes&structure=Ubuntu+Help&page_ref_id=18](http://shallows.bounceme.net/tiki-index.php?page=Enable+Emerald+Themes&structure=Ubuntu+Help&page_ref_id=18)

I have it running on my system and it works great.

Hope this helped.

---

### Post by underage17 on 2011-07-10
> **fullerenedream said:**
> This is the best fix I found so far, and it's disappointing. I followed the instructions and it got emerald  working. But I want to switch back and forth between emerald and metacity themes, so then I tried metacity --replace. That worked, but now emerald --replace doesn't reenable emerald for me.

Ubuntu 11.04 Fix: Enable Emerald Themes for Compiz-Fusion Window Borders (Title-Bars)
[http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/](http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/)

For some reason, one of the steps in between didn't work. It said try --fix-missing or something but that didn't help either. :\

> **steinerd said:**
> Here is a tutorial to get emerald working on 11.04.

[http://shallows.bounceme.net/tiki-index.php?page=Enable+Emerald+Themes&structure=Ubuntu+Help&page_ref_id=18](http://shallows.bounceme.net/tiki-index.php?page=Enable+Emerald+Themes&structure=Ubuntu+Help&page_ref_id=18)

I have it running on my system and it works great.

Hope this helped.

This started giving problems halfway thru.

Is it because I'm on 64 bit?

---

### Post by Frogs Hair on 2011-07-10
I have tested this , but I'm not sure how it will work considering that have made changes . If you choose to use the PPA you may want remove Emerald , reinstall it , and  then add the PPA .

[http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html#more](http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html#more)

---

### Post by underage17 on 2011-07-13
> **Frogs Hair said:**
> I have tested this , but I'm not sure how it will work considering that have made changes . If you choose to use the PPA you may want remove Emerald , reinstall it , and  then add the PPA .

[http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html#more](http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html#more)

IT WORKED!! I finally got emerald to work
thanks a ton :)

---

### Post by Frogs Hair on 2011-07-13
> **underage17 said:**
> IT WORKED!! I finally got emerald to work
thanks a ton :)

You're Welcome :)

---

