---
title: "Which guide should I use for XGL/Compiz?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by [Nirvana] on 2006-06-02
I have a 1.6Ghz celeron M processor with an ATI Radeon Xpress 200M graphics card. I have 512 MB/RAM but 64 is for the graphics card. Which guide should I use for XGL/Compiz (what I'm trying to achieve is Vista-Like affects, that is translucent, blurry (maybe, if Compiz/my setup supports it) and cube rotating goodness). I have [read](http://doc.gwos.org/index.php/EyeCandyDapper) and [read](http://www.ubuntuforums.org/showthread.php?t=131253), but I am torn between the two guides, which one should I use? I guess the ATI, because it seems more specific to my hardware, but I would like third party help (and unfortunately can't go on IRC ](*,) )

Also, I'm on KDE not GNOME, so what changes must I make (I also read the Nvidia/KDE guide, just to see the KDE-specific stuff, needless to say, I was blind to it)

---

### Post by Anduu on 2006-06-02
Opps one minute heh

---

### Post by Anduu on 2006-06-02
Check this one out

[http://www.compiz.net/viewtopic.php?id=205](http://www.compiz.net/viewtopic.php?id=205)

---

### Post by [Nirvana] on 2006-06-03
Looks pretty detailed, even a fix if you want to use KDM later down in the topic... It's PRINTING TIME!

---

### Post by [Nirvana] on 2006-06-03
alright, we're starting with the problems: When I type:
```
sudo gconftool --set --type list --list-type string /apps/compiz/general/allscreens/options/active_plugins '[gconf,miniwin,decoration,transset,fade,minimize,cube,rotate,zoom,scale,move,resize,place,switcher,trailfocus,water]'
```

I get an error: Don't understand type `list'

---

### Post by [Nirvana] on 2006-06-03
alright, I followed the rest of the guide, and now I have NO windows manager. My windows have no borders or minimize/close/maximize buttons. Any ideas?

---

