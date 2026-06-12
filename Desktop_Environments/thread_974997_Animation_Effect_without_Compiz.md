---
title: "Animation Effect without Compiz?"
date: 2008-11-08
forum: Desktop Environments
---

### Post by kenokabe on 2008-11-08
Hi List.

Is there any way to add Animation ettcts on gnome desktop WITHOUT compiz-fusion?

I have used compiz for a while, but the only headaque is firefox with 'yet Another Smooth Scrolling'.

With a proper setting, firefox with this addon performs very smooth scroll feeling similar to iPhone scrolling.

However, under compiz, the scroll smoothness is vanished.
I tried every way to tweak configuration, but concluded I take the smooth scroll and disable compiz.

Having said that, I still need some animation effect.

I recall ubuntu used to have some animation effect under gnome without compiz stuff, so I guess there might a way to add extra eye-candy effect without Compiz.

Please advice. Thanks!

Ken

---

### Post by ad_267 on 2008-11-08
What sort of effects do you want? If you press Alt+F2 and run gconf-editor then navigate to apps - metacity - general - compositing_manager you can enable compositing in Metacity which will give your windows shadows and allow some other subtle effects. Another option to look at is xcompmgr.

---

### Post by kenokabe on 2008-11-08
ad_267
Thanks for replying.

I have checked gconf-editor before, and thought insufficient.

xcompmgr looks better.

Effects I want are terminal-console with transparent background or window fading-in.folding-out stuff.

Don't you know a good way to turn compiz on without interfaring events inside of a window, such as firefox-scroll?

Ken

---

### Post by ad_267 on 2008-11-08
No I don't think you can enable compiz like that. Metacity compositing gives a transparent terminal background, but won't do the fading in and out.

---

### Post by kenokabe on 2008-11-08
> **ad_267 said:**
> No I don't think you can enable compiz like that. Metacity compositing gives a transparent terminal background, but won't do the fading in and out.

Thanks for your input. Understood. 
I will research more.

Ken

---

### Post by CyberBone on 2009-03-17
> **kenokabe said:**
> ad_267
Thanks for replying.

I have checked gconf-editor before, and thought insufficient.

xcompmgr looks better.

Effects I want are terminal-console with transparent background or window fading-in.folding-out stuff.

Don't you know a good way to turn compiz on without interfaring events inside of a window, such as firefox-scroll?

Ken
hi 

to you use xcompmgr, you only can execute one effect for time...
:)

---

### Post by hariks0 on 2009-12-16
Is it possible to enable or disable an effect/plugin without ccsm. An option to upload a profile will also do.

Thanks in advance.

---

