---
title: "KDE shortcuts on my Gnome menu: how to get rid of them?"
date: 2005-04-23
forum: Desktop Environments
---

### Post by robertobech on 2005-04-23
I have Ubuntu installed, and downloaded kubuntu, so now I have both on my system. However, as soon as I installed kubuntu, all kde shortcuts appeared also on my gnome menu, and I would like to get them out, so I only have gnome programs listed under my gnome menu.

I've downloaded gnome menu editor, and it works fine... with gnome programs. But I can't take KDE aprograms out of the menu! How can I do it?

And how can I edit the gnome menu by hand, without the aid of a program?

Thanks a lot!

---

### Post by cutOff on 2005-04-23
You can try to remove them from /usr/share/applications directory.

---

### Post by robertobech on 2005-04-23
There is a kde folder under /usr/share/applications/. But if I delete the files inside of it (for example, kppp) the application won't show up on the kde menu, right? The idea is that kde applications show on kde menu, and that gnome apps show on gnome menu, that is, I want kppp out of my gnome menu, but on my kde menu.

---

### Post by yage on 2005-04-24
You can use Gnome menu-editor!  :grin: [http://www.ubuntuguide.org/#menu-editor](http://www.ubuntuguide.org/#menu-editor)

---

### Post by gunnyman on 2005-04-24
Taken from another thread:
```
cd /usr/share/applications/kde
sudo chmod a+rw /usr/share/applications/kde/*
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
sudo chmod 644 /usr/share/applications/kde/*
``` 

worked perfectly for me.

---

