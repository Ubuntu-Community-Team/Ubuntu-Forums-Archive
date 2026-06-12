---
title: "where do I find screensavers"
date: 2008-12-08
forum: General Help
---

### Post by scottac on 2008-12-08
I am very new to linux and I am trying to figure out where to find screensavers. 

I search in adept and nothing is turning up. how would I go about finding screensavers, or how might I install a screensaver package.  

Again, I am extremely new to linux. Try to be as specific as possible.  

Thanks, this forum is great...

---

### Post by gettinoriginal on 2008-12-09
I assume you are talking about other than those already on here.  System > Preferences > Screensaver

Try these, themes, wallpaper, screensavers etc;

[http://art.gnome.org/](http://art.gnome.org/)

[http://www.deviantart.com/](http://www.deviantart.com/)

[http://ubuntuforums.org/showthread.php?t=203093](http://ubuntuforums.org/showthread.php?t=203093)

---

### Post by sayakb on 2008-12-10
Install this package:
```
sudo apt-get install kscreensaver
```

---

### Post by sayakb on 2008-12-10
You can select the screensaver from System Settings -> Desktop -> Screensaver

---

### Post by scottac on 2008-12-10
> **LinuxIsInnovation said:**
> Install this package:
```
sudo apt-get install kscreensaver
```

Ok this installed screensavers just fine.  However, when I go to Applications -> Settings -> Screensaver I get some errors.

Every time I select any of the buttons in screensaver preferences window I get this message:

[B]Error:

Directory does not exist: "/usr/share/backgrounds"
[/B]

mmmm

any ideas

---

### Post by infoseeker on 2009-05-20
I am having this problem too, and I found:

> Do you have the screensaver-default-images package installed? It is part of ubuntu-desktop and xubuntu-desktop. For some reason screensaver-default-images depends on xscreensaver-data and not the other way around...

```
$ sudo apt-get install xscreensaver-data-extra xscreensaver-gl-extra screensaver-default-images xscreensaver-data
```

I just have to get xscreensaver to startup when Kubuntu starts ;)

---

### Post by SuperSonic4 on 2009-05-20
Can you post the output of ```
which xscreensaver
```

I don't have xscreensaver installed and mine works as it should

---

