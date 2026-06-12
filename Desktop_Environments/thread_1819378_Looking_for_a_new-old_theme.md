---
title: "Looking for a new-old theme"
date: 2011-08-06
forum: Desktop Environments
---

### Post by Number3124 on 2011-08-06
I've been using the Dust theme with Ubuntu Classic in 11.04 for a while now, and I'm looking for a new theme. I like some parts of Dust (the position of the controls in the title bar, the upper panel's controls and icons, ect.), but I really want a theme that simulates the look and, especially, the feel of 7.04 and 8.04. 

Thanks

---

### Post by Frogs Hair on 2011-08-06
Try the links , You have the best idea of what you want . 

[http://ubuntu-art.org/](http://ubuntu-art.org/)

[http://gnome-look.org/](http://gnome-look.org/)

---

### Post by Krytarik on 2011-08-06
If you want to use the original default themes of Feisty 7.04 or Hardy 8.04, you can download them from the links below. I hope, you know or will get how to implement them. You may want to use both, "human-theme" and "human-icon-theme".

Feisty 7.04:
[http://old-releases.ubuntu.com/ubuntu/pool/main/h/human-theme/human-theme_0.6_all.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/h/human-theme/human-theme_0.6_all.deb)
[http://old-releases.ubuntu.com/ubuntu/pool/main/h/human-icon-theme/human-icon-theme_0.18-0ubuntu1_all.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/h/human-icon-theme/human-icon-theme_0.18-0ubuntu1_all.deb)

Hardy 8.04:
[http://packages.ubuntu.com/hardy/human-theme](http://packages.ubuntu.com/hardy/human-theme)

Greetings.

---

### Post by Number3124 on 2011-08-06
Thanks for the links. The icon package worked very well and it looks great, but the theme required the gtk2 package which dpkg seems to think I do not have installed on my system. Should I assume I have gtk3 and look for a version that supports gtk3? Thanks again for the links.

---

### Post by Krytarik on 2011-08-07
Sorry, I was a bit short-worded yesterday night! I could have at least linked to this guide:
[http://ubuntu4beginners.blogspot.com/2011/06/install-older-newer-ambiance-radiance.html](http://ubuntu4beginners.blogspot.com/2011/06/install-older-newer-ambiance-radiance.html)

You only need to adapt some things here and there, but generally it's the way I meant, and the only way I recommend.

There should be no issues regarding missing dependencies then.

And no, you are still using GTK+ 2, GTK+ 3 is going to be used from the next release of Ubuntu, Oneiric Ocelot 11.10, onwards.

---

### Post by Frogs Hair on 2011-08-07
If those themes were made to run on Gnome 2.0 and you are using Gnome 2.32 , that may explain why they do not work .

Both releases predate my Ubuntu experience , so I don't know what version of Gnome was in use at the time of either .

---

### Post by Number3124 on 2011-08-07
Thanks for the help guys. I dug a little more and tweaked the Software Center's settings, and the dependancy I'm missing is the human-cursor theme. I've been looking, but I can't find it.

---

### Post by Krytarik on 2011-08-07
> **Number3124 said:**
> I dug a little more and tweaked the Software Center's settings, and the dependancy I'm missing is the human-cursor theme. I've been looking, but I can't find it.
If you want to go that way, and since it seems like you are talking about the Feisty version, here it is:
[http://old-releases.ubuntu.com/ubuntu/pool/main/h/human-cursors-theme/human-cursors-theme_0.5_all.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/h/human-cursors-theme/human-cursors-theme_0.5_all.deb)

Good luck by that way!

---

### Post by Number3124 on 2011-08-07
Thanks for the assist. It's all working perfectly. Thank you all.

---

