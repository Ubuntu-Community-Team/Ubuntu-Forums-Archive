---
title: "Installing XGL/ XGL's &quot;Expose-like&quot; Feature"
date: 2007-12-21
forum: Desktop Effects &amp; Customization
---

### Post by Vazguard on 2007-12-21
Hey all:

I recently found out about XGL's "expose-like" window switcher, so I have been looking all over the internet for a method to install it.  I found a few, but they all have missing links and other weird stuff.  I have Compiz-fusion installed already.  If anyone could enlighten me on a way to actually install and run this XGL so I can have the window switcher, that'd be great.

Thanks,

Vaz

---

### Post by santiagoward2000 on 2007-12-22
Hi!
I think what you're trying to install is **Compiz-Fusion**. **XGL** is just the software that allows your desktop to use OpenGL. It is only needed on some ATI drivers. As you are using an NVidia card, you won't need it.
As you are using Gusty, **Compiz-Fusion** must be already installed. To configure it, you should install **compizconfig-settings-manager**. You can look for it in **Synaptic**, or just open a terminal and type:
```
sudo apt-get install compizconfig-settings-manager
```
Then, just open it and look for the **Expo** plugin to get it working.
Cheers!

---

### Post by Vazguard on 2007-12-22
I have compiz-fusion already installed, but I the expo option in the manager is not exactly what I'm talking about.  Either that or I'm just completely missing the option to set it like so.

What I want is what is demonstrated in this YouTube video, about 1 minute and 15 seconds in:

[http://www.youtube.com/watch?v=Cz_2vKq5cZk]("http://www.youtube.com/watch?v=Cz_2vKq5cZk")

Expo for me just lays out my dektop cube in a line of panels, not like in the video where it "tiles" the windows in the current desktop panel to easily choose the desired one, like Mac's "Expose" feature.

I hope this helps.

---

### Post by Mr Greencastle on 2007-12-22
I guess were just confusing the names. "Expo" != "Expose"

I think the plugin you are looking for is called "Scale"

Hope that helps!

Mr Green

---

### Post by santiagoward2000 on 2007-12-22
> **Mr Greencastle said:**
> I guess were just confusing the names. "Expo" != "Expose"

I think the plugin you are looking for is called "Scale"

Hope that helps!

Mr Green

Yes! He's right! The plugin on the video is **Scale**.

---

### Post by Vazguard on 2007-12-26
Yes that's it!  Thank you so much.

---

