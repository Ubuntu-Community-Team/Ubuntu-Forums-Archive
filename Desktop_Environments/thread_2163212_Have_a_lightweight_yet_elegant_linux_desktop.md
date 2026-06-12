---
title: "Have a lightweight yet elegant linux desktop"
date: 2013-07-17
forum: Desktop Environments
---

### Post by c beginner on 2013-07-17
I've been running Unity on my 512mb notebook and as expected performance was way below par. I tried many different ways to reduce memory consumption, but it didnt make real difference. So my only choice was to install a lighter desktop. I installed XFCE and it was quiet snappy but not enough eye-candy to appeal to my tastes :KS

Made quite a few tweaks and now it looks great, actually feels a whole lot better than Unity.

[[IMG]http://i44.tinypic.com/2s7j6sk.png[/IMG]]("http://i44.tinypic.com/2s7j6sk.png")

I know not everyone care about looks but thought maybe me sharing this can help someone else.
Here's what I've done:
```

// Install Xfce
sudo apt-get install xfce4

Once finished, it's time to log in to your newly installed XFCE desktop.

// Install Ambiance & Radiance Themes (ravefinity)
sudo add-apt-repository ppa:ravefinity-project/ppa && sudo apt-get update
sudo apt-get install ambiance-xfce-lxde radiance-xfce-lxde

// To activate, go to 'XFCE Settings Manager' then --> 'Appearance'
In the 'Style Tab' choose either 'ambiance-xfce-lxde' or 'radiance-xfce-lxde'. I prefer ambiance.
I use 'Ubuntu-Mono-Light' for icnons but you can choose whatever you prefer.

'Settings Manager' --> 'Window Manager' --> 'ambiance-xfce-lxde'

Note the panels may look weird. To fix it you have to set the panel background manually.

Right Click on the Xfce Panel --> Then select 'Panel Preferences' --> In the 'Appearance' tab click on the style drop-down menu and select 'Background Image'. 
Then browse through following directory and path to locate 'panel.png'. 
/usr/share/themes/ambiance-xfce-lxde/gtk-2.0/apps/img

If you're going to increase the panel size, use 'panel-big.png'.  And adjust it to your liking.


```

That's it! you'll now have a fast, light yet beautiful desktop.

---

