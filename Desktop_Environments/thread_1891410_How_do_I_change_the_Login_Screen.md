---
title: "How do I change the Login Screen?"
date: 2011-12-05
forum: Desktop Environments
---

### Post by IanVaughan on 2011-12-05
I have no "Login Window" as this [post suggests]("http://www.simplehelp.net/2009/05/21/how-to-change-the-ubuntu-login-screen/")!
Although I am using the new Gnome, by GnomeDo doesnt find it!

---

### Post by MG&amp;TL on 2011-12-05
Err...that's GDM, which was phased out in Oneiric.

Edit /etc/lightdm/unity-greeter.conf, then change the image field to pic of choice. Done. :D

---

### Post by cortman on 2011-12-05
That post was written in 2009. The times they have a-changed.
A quick google search and you get [this,]("http://www.liberiangeek.net/2011/09/change-the-login-screen-background-in-ubuntu-11-10-oneiric-ocelot/") which is what I used to change my login background. I assume that's what you're asking.

---

### Post by IanVaughan on 2011-12-05
> **cortman said:**
> That post was written in 2009. The times they have a-changed.
A quick google search and you get [this,]("http://www.liberiangeek.net/2011/09/change-the-login-screen-background-in-ubuntu-11-10-oneiric-ocelot/") which is what I used to change my login background. I assume that's what you're asking.

That looks like the thing!
But I cant see how changing the background jpg can change the theme? How does one change that?

---

### Post by MG&amp;TL on 2011-12-05
That's pretty much all you can do without some serious hacking at the moment, but they're working on it. I can think you can get different lightdm.conf downloads..

---

### Post by IanVaughan on 2011-12-05
> **MG&TL said:**
> That's pretty much all you can do without some serious hacking at the moment, but they're working on it. I can think you can get different lightdm.conf downloads..

1) Thats rubbish, they remove support for customisation before having something ready to replace it!
2) That pic has a different placement and boarder style on the username prompt from the default, so they have managed something.

---

### Post by MG&amp;TL on 2011-12-05
> **IanVaughan said:**
> 1) Thats rubbish, they remove support for customisation before having something ready to replace it!
2) That pic has a different placement and boarder style on the username prompt from the default, so they have managed something.
If you want, with some extra googling, you can make awesome stuff by editing the configuration files (as with everything in ubuntu), but it won't be easy.

You can still install gdm if you want, and presumably the login screen editor too. :D

Sorry, I tell a lie, you can change the 'theme' too, although that's misleading, a slightly different white and mildly different boxes is that it amounts to. Just take a gander at the config file (/etc/lightdm/unitygreeter.conf), and see what you fancy changing. Just be careful that what you type exists, otherwise I suspect something bad will happen.

---

### Post by Frogs Hair on 2011-12-05
I use the login settings in Ubuntu Tweak , but make sure you get the correct version per the links on the main page . [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

