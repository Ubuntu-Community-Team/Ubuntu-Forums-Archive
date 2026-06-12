---
title: "I want the best of both worlds gtk &amp; qt"
date: 2013-03-12
forum: Desktop Environments
---

### Post by giantjoebot on 2013-03-12
I need to do a fresh install. In every variant I try there is something that I love, and feel like I just can't live without.  So it makes it difficult to choose which Ubuntu version I'm going to use.  I'm currently using Mint KDE 13, but I'm thinking about switching to Kubuntu, if not something else.  In the past I tried to stick with either qt or gtk, but I just don't care anymore.  So I'm just going to say screw it, and I want to install both.  So I can use whatever I want, and not worry about it.  I've had problem in the past running gtk applications like transmission in kde.  So what would I need to do in order to install say gtk on kde so that everything runs smooth?  Or is that even possible?  Would I have to use something like xfce or lxde to be able to take advantage of both?

---

### Post by zombifier25 on 2013-03-12
If you want GTK+ apps to look natively in KDE, install the gtk2-engines-oxygen and the gtk3-engines-oxygen packages.

GTK+ apps can run perfectly in Qt-base environments and vice versa. There won't be any problems, probably aside from slightly longer loading times (which is barely noticable in 2013), but that's it. What matters is the DE you are using, not what toolkit it's based on.

---

### Post by giantjoebot on 2013-03-12
Thank you.  I did however notice an error when running transmission gtk in Mint KDE.  When I looked into it I found out that it might have been because it was using an old version of gtk.   I was thinking that there might be a way to update or upgrade gtk in Kubuntu or Mint KDE to be the same as Ubuntu.  

I ended up installing the qt version, but it lacks some of the functionality of the gtk+ version.  ktorrent barely worked at all for me. 

Does anyone know, by chance, how to add the "open terminal here" when you right click, like in xubuntu, in Kubuntu or Mint KDE.  I really like that in xubuntu.  I keep finding myself right clicking, and then remembering, "oh yeah I'm not in xubuntu".

---

