---
title: "gnome-themes-extras package for 16.04 Xenial Xerus? Looking for Clearlooks and Gion"
date: 2016-07-16
forum: Desktop Environments
---

### Post by mdlueck on 2016-07-16
Greetings,

I make use of Clearlooks and Gion to theme Xubuntu. They are found in package: gnome-themes-extras

There does not appear to be that package for 16.04 Xenial Xerus. According to: [https://launchpad.net/ubuntu/xenial/+source/gnome-themes-extras](https://launchpad.net/ubuntu/xenial/+source/gnome-themes-extras)

Where do these Clearlooks and Gion theme components come from now in the 16.04 release of Xubuntu?

I am thankful,

---

### Post by vasa1 on 2016-07-16
> **mdlueck said:**
> Greetings,

I make use of Clearlooks and Gion to theme Xubuntu. They are found in package: gnome-themes-extras

There does not appear to be that package for 16.04 Xenial Xerus. According to: [https://launchpad.net/ubuntu/xenial/+source/gnome-themes-extras](https://launchpad.net/ubuntu/xenial/+source/gnome-themes-extras)

Where do these Clearlooks and Gion theme components come from now in the 16.04 release of Xubuntu?

I am thankful,I've come across Clearlooks but didn't know about Gion. Anyway, I suspect Clearlooks won't be of much help because the "default" Clearlooks doesn't support GTK-3 and Xubuntu has quite a few applications that use GTK-3.

If you want, look at "clearlooks-phenix-theme" which is described as a "GTK3 port of Clearlooks theme":
```
$ apt search clearlooks
Sorting... Done
Full Text Search... Done
clearlooks-phenix-theme/xenial 6.0.3-1 all
  GTK3 port of Clearlooks theme

gtk-clearlooks-gperfection2-theme/xenial 1.1-0ubuntu2 amd64
  gtk theme for the clearlooks engine
$ 
```

---

### Post by mdlueck on 2016-07-16
> **vasa1 said:**
> If you want, look at "clearlooks-phenix-theme" which is described as a "GTK3 port of Clearlooks theme":


Thank you very much... Xubuntu 16.04 looking better already. And I can actually grab the corner of the windows to resize two sides at once.

Xfce in 16.04 does not seem to have ability to select a different collection of icons. Resizing at the corners was more important than the icon set.

I am thankful,

---

