---
title: "Emerald theme manager not applying themes."
date: 2008-02-18
forum: Desktop Effects &amp; Customization
---

### Post by ZimmerX on 2008-02-18
Hey, 

I have Ubuntu 64-bit Gutsy.

I recently fixed my Compiz problem - I have an 8800GTS, so it wasn't running with XGL - and I got my desktop effects all working flawlessy. 

There is one problem though:
I installed Emerald theme manager, to be able to apply some themes from "gnome-look". The themes are .bin files and are automatically detected by Emerald theme manager. The problem is, that when I open one, nothing happens.
The theme will not change from what I am using ( configured through the default APPEARANCE settings in Ubuntu ).

How do I override that theme and allow Emerald theme manager to work properly?

Also, how can I create more than 2 desktop windows?

Any help would be greatly appreciated.

Many thanks in advance.

---

### Post by FuturePilot on 2008-02-18
Try
```
emerald --replace
```
For more desktops
```
sudo apt-get install compizconfig-settings-manager
```
System&#8594;Preferences&#8594;Advanced Desktop Effects Settings. Go under the General section and click on the Desktop Size tab

---

### Post by ZimmerX on 2008-02-18
Thanks. One thing I find weird though, is that when I replace the theme, it changes to that theme, but when I close the terminal, the theme disappears and I get an erroneous desktop.

So I have to restart to fix the settings. I find that a bit weird, but anyways, your answer proved perfect. Thanks a bunch.

---

### Post by jcrow on 2008-02-18
Instead of typing in terminal, use alt f2

---

