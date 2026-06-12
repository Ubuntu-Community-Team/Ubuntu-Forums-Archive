---
title: "How do I change the theme of KDE apps in Gnome?"
date: 2008-01-14
forum: Desktop Environments
---

### Post by rainwalker on 2008-01-14
I've read stuff about something called kcontrol, is this what I need?

---

### Post by family on 2008-01-14
Not sure, I the only one I use is Amarok, and that is easily configureable. Does the GNOME Theme changer not work with it?

---

### Post by rainwalker on 2008-01-14
> **family said:**
> Not sure, I the only one I use is Amarok, and that is easily configureable. Does the GNOME Theme changer not work with it?

Same here, but I'd still like to be able to theme it. And no, the Gnome themes don't affect KDE apps (they use Qt instead of GTK)

---

### Post by imtheguru on 2008-01-14
> **rainwalker said:**
> I've read stuff about something called kcontrol, is this what I need?Probably not; that's the KDE control panel.

Look for qt3-config

Cheers.

---

### Post by rainwalker on 2008-01-14
> **imtheguru said:**
> Look for qt3-config

It's not in Synaptic

---

### Post by TeaSwigger on 2008-01-14
Yes it is, but it's called qt3-qtconfig. There's also qt4-qtconfig for qt4 apps, but you'll likely just need qt3 at this time.

---

### Post by rainwalker on 2008-01-14
> **TeaSwigger said:**
> Yes it is, but it's called qt3-qtconfig. There's also qt4-qtconfig for qt4 apps, but you'll likely just need qt3 at this time.

Ok, I got it installed and I can run it. Now, do you know how to add more themes/visual styles to the dropdown list?

---

### Post by TeaSwigger on 2008-01-14
Well I use KDE / Kubuntu not the qt3 config tool, but the two "usual ways" should still work:

- Install themes via Synaptic. Search for KDE style, that should scare some up like kde-style-serenity for example. The KDE styles are qt.

- Install more themes from third parties. [http://www.kde-look.org](http://www.kde-look.org) is one place to search. Install methods may vary.

Once installed they should show in qt3-qtconfig.

---

### Post by rainwalker on 2008-01-14
> **TeaSwigger said:**
> - Install more themes from third parties. [http://www.kde-look.org](http://www.kde-look.org) is one place to search. Install methods may vary..

What are some of those methods?

---

### Post by TeaSwigger on 2008-01-14
> **rainwalker said:**
> What are some of those methods?

That's for the author of a given theme to explain ;) but for instance, some are convenient .deb packages made for Kubuntu, which should work just fine for qt apps running in ubuntu as well, while others might involve manually placing files in certain locations. I don't know how to manually install them since I've only installed a couple from there so far, and both were packaged to easily install in KDE / Kubuntu's style manager. Enjoy the eye-candy. :)

---

### Post by rainwalker on 2008-01-14
Alright, thank you!

---

### Post by rainwalker on 2008-01-15
Ok, I guess I just don't understand KDE; I'm trying to install the Amarok theme from [http://www.kde-look.org/content/show.php?content=60013](http://www.kde-look.org/content/show.php?content=60013)
Do you know how to do this?

---

### Post by TeaSwigger on 2008-01-15
> **rainwalker said:**
> Ok, I guess I just don't understand KDE; I'm trying to install the Amarok theme from [http://www.kde-look.org/content/show.php?content=60013](http://www.kde-look.org/content/show.php?content=60013)
Do you know how to do this?

Yea, Amarok kinda has it's own thing apart from the rest of KDE. It looks to me like it should be, hopefully, as easy as downloading the Amarok theme on that page there, going into Amarok, Settings > Configure Amarok > Appearance, and then under "context browser style" clicking "install new style," select the downloaded file and bingo. Don't have to unzip, tar or whatever it, just point it to the downloaded file. :)

---

