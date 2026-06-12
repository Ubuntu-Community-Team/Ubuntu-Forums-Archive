---
title: "Firefox not using same theme"
date: 2009-12-07
forum: Desktop Environments
---

### Post by Cetra on 2009-12-07
Hey guys,

Having issues with the new firefox on Ubuntu Karmic.  It's like it doesn't want to match the appearance of every single other window.

Is there a fix for this?

---

### Post by lovinglinux on 2009-12-07
Try [Stylish](https://addons.mozilla.org/en-US/firefox/addon/2108).

---

### Post by Cetra on 2009-12-07
Im more interested in why it's not working post upgrade than spending a day tweaking my settings.  I thought that the look and feel of ubuntu was meant to be unified?  Why is Firefox displaying things differently anyway?

---

### Post by akashiraffee on 2009-12-07
Because you are using KDE.  Firefox is GTK based, but KDE uses the Qt library for its GUI.

Login into a gnome session and set your theme there -- they may not be the same as the KDE themes, but pick whatever, something that matches.  This is the theme firefox will use when you log back into KDE.

---

### Post by lovinglinux on 2009-12-07
> **akashiraffee said:**
> Because you are using KDE.  Firefox is GTK based, but KDE uses the Qt library for its GUI.

Login into a gnome session and set your theme there -- they may not be the same as the KDE themes, but pick whatever, something that matches.  This is the theme firefox will use when you log back into KDE.

I don't see any mention of KDE in the OP post. Besides, Firefox is not really GTK. As far as I know it mimics the GTK theme. If the problem was GTK/QT related, the problem wouldn't be restricted to the menu color, but the entire interface.

Additionally, if the user was really using KDE, then setting up the theme under Gnome and logging back to KDE wouldn't solve the problem. KDE users must install qtcurve engine to make gnome applications look like KDE. But this is not the case here.

Color problems are common among Firefox users that install dark themes. There is another way of fixing this, by changing userChrome.css in your Firefox profile. this is essentially what Stylish does with the correct script. [Here](http://ubuntuforums.org/showthread.php?t=503508) you can find a how-to. if that doesn't help, see [similar threads](http://www.google.com/search?q=Firefox+dark+theme+site%3Aubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0).

---

### Post by Cetra on 2009-12-07
I am using Gnome, my apologies for not being clear.  I thought that people would assume I'm using Gnome since it's the default with Ubuntu.

The problem with using stylish is that I don't actually stick to the one theme very long and it's not really an ideal solution.  Should I possibly log this as a fault with Firefox development?  If they're not using GTK, but a mimicry of it, shouldn't they mimic it to a better standard?

---

### Post by akashiraffee on 2009-12-07
> **Cetra said:**
>   Should I possibly log this as a fault with Firefox development?  If they're not using GTK, but a mimicry of it, shouldn't they mimic it to a better standard?

Hey, we are sort of lucky they put work into supporting linux at all.  Maybe you'd like to give "Iceweasel" another try instead :p

---

### Post by Cetra on 2009-12-09
Hmm,

Yeah

I guess I'll switch to chromium when that's matured, if they don't fix it by then.

I think I have mild OCD :o


Thanks for answering my questions anyways.

---

