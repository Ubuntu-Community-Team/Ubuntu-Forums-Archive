---
title: "screensavers and notify-osd"
date: 2011-08-27
forum: Desktop Environments
---

### Post by Pragu on 2011-08-27
Hello all, I recently installed the lubuntu desktop environment in favour of ubuntu in the hopes of saving battery power, and it has worked quite well, by and large. I have run into two problems, however: 
1) Whenever I wake my computer from sleep, the screensaver starts up and I have to wiggle the mouse. It isn't a big problem, but it is annoying. I believe it has something to do with the interaction of gnome-screensaver and xscreensaver (with the xscreesaver coming on after sleep). How can I permanently disable one, and which one should I disable?  

2) Whenever I lose internet or change the brightness, it brings up the notify-osd process (as it did in ubuntu). However, these messages persist until I run killall "notify-osd". I've been in the preferences for the package and nothing seems to work, is there a better notifier, or at least a way to kill the process without it cropping up whenever I change the brightness?

thanks!

---

### Post by jerrrys on 2011-08-28
edit: i missed the lubuntu part

---

### Post by kerry_s on 2011-08-28
> **Pragu said:**
> Hello all, I recently installed the lubuntu desktop environment in favour of ubuntu in the hopes of saving battery power, and it has worked quite well, by and large. I have run into two problems, however: 
1) Whenever I wake my computer from sleep, the screensaver starts up and I have to wiggle the mouse. It isn't a big problem, but it is annoying. I believe it has something to do with the interaction of gnome-screensaver and xscreensaver (with the xscreesaver coming on after sleep). How can I permanently disable one, and which one should I disable?  

2) Whenever I lose internet or change the brightness, it brings up the notify-osd process (as it did in ubuntu). However, these messages persist until I run killall "notify-osd". I've been in the preferences for the package and nothing seems to work, is there a better notifier, or at least a way to kill the process without it cropping up whenever I change the brightness?

thanks!


install straight lubuntu, lubuntu on top of ubuntu ain't no difference because stuff still runs in the background. straight lubuntu does not have a lot of extras in the background.

---

### Post by Pragu on 2011-08-29
thanks, is there any way to install just lubuntu and keep all my current files?

---

### Post by raja.genupula on 2011-08-30
```
sudo apt-get install lubuntu-desktop
```

this is a meta pkg . so you loss nothing . your files will be there . you can choose what session you what at login screen , ubuntu or lubuntu

---

### Post by Pragu on 2011-08-31
Thank you all for the replies! That's exactly what I did, raja.genupula, but does that run all the ubuntu scripts underneath, like kerry_s says?

---

### Post by kerry_s on 2011-08-31
> **Pragu said:**
> Thank you all for the replies! That's exactly what I did, raja.genupula, but does that run all the ubuntu scripts underneath, like kerry_s says?

Installing lubuntu-desktop on top of gnome just adds to gnome. 
I run straight lubuntu & there is a difference, you'll see it in the boot time & just general use, it feels faster with less gnome.

---

### Post by Pragu on 2011-08-31
Can I get Lubuntu without Gnome without doing a fresh install?

---

### Post by kerry_s on 2011-08-31
> **Pragu said:**
> Can I get Lubuntu without Gnome without doing a fresh install?

the closest you could get would be this:
[http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

but like i said, i think a clean install is the best way.

---

