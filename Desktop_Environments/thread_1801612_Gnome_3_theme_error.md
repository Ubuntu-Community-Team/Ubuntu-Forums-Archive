---
title: "Gnome 3 theme error?"
date: 2011-07-10
forum: Desktop Environments
---

### Post by Mindswap1 on 2011-07-10
Hey guys so I wanted to check out Gnome 3, and well I don't think it installed correctly this is what it looks like for me. It looks okay, but the title bar is orange, and everywhere I look everyone has a beautiful white theme. like in this video. 

> [http://www.youtube.com/watch?v=ALCUPp-5UwE&feature=related](http://www.youtube.com/watch?v=ALCUPp-5UwE&feature=related)As you can see the guy has a nice white theme. How can I fix this. I tried reinstalling the themes with the following codes, but it didn't work. 
```

gksudo apt-get remove gnome-accessibility-themes
gksudo apt-get install gnome-themes-standard
```

---

### Post by uRock on 2011-07-11
Bump for move to *Desktop Environments*.

---

### Post by Githlar on 2011-07-12
I have the same problem, only instead of solid orange, it's striped orange and it's highly annoying! I hope this gets resolved.

---

### Post by isaacj87 on 2011-07-12
> **Mindswap1 said:**
> Hey guys so I wanted to check out Gnome 3, and well I don't think it installed correctly this is what it looks like for me. It looks okay, but the title bar is orange, and everywhere I look everyone has a beautiful white theme. like in this video. 

As you can see the guy has a nice white theme. How can I fix this. I tried reinstalling the themes with the following codes, but it didn't work. 
```

gksudo apt-get remove gnome-accessibility-themes
gksudo apt-get install gnome-themes-standard
```

I remember having the same problem when I played around with Gnome 3 on Ubuntu 11.04. Install the gnome-tweak-tool. Open it and go to the "Interface" section. Change the GTK+ theme to "Adwaita."

---

### Post by Githlar on 2011-07-12
Got it!

```
sudo apt-get remove gnome-accessibility-themes
sudo apt-get install gnome-themes-standard
```

From: [http://www.ubuntugeek.com/how-to-fix-common-gnome-3-issues-on-ubuntu-11-04-natty.html](http://www.ubuntugeek.com/how-to-fix-common-gnome-3-issues-on-ubuntu-11-04-natty.html)

---

