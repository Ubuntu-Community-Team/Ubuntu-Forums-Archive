---
title: "Questions from Kubuntu newbie"
date: 2005-07-22
forum: Desktop Environments
---

### Post by veritas366 on 2005-07-22
HI...I started with Ubuntu and wanted to check out Kubuntu...so I did it via Synaptic...I don't know if this does anything different than a fresh install of Kubuntu.

I'm having a few issues...mainly with Konqueror.  

First off, I think it's cool that Konqueror has so many functions, but they don't work right for me.

When I try to utilize my CDRW I click on it and Konqueror pops up and tells me that's not a valid address.  

It also crashes a lot...I can't quite isolate a reason yet.  Just certain sites.

Finally, can someone tell me how to enable java and flash and what media embedding works...can I have any streaming media in Konqueror?

I could continue using FIrefox, but it doesn't look very good in KDE...especially the font.  I guess I can live with it as I like the overall look of the desktop.  I saw instructions for adding Kubuntu specific repos but I wasn't sure how to make sure I'm getting Firefox tweaked for Kubuntu..if there is such a thing.  

Thanks for suggestions.

---

### Post by Altmenorg on 2005-07-22
Concerning the stability problems, I never saw that (I mean it can happen, but is very rare...), but I have a "from scratch" Kubuntu installation.
It is certainly better to install a fresh system that installing , but technically, that shouldn't happen...
The crashes happened to me to, but was solved after updated to kde 3.4.1...

I strongly suggest you to reinstall Kubuntu directly and upgrade you kde version, adding this to the repo list (/etc/apt/sources.list):

```
deb http://kubuntu.org/hoary-kde341/ hoary-updates main
```

Next, concerning the gtk look in kde, yes, it is absolutly awfull ;)
The best thing to go arround is to install the "gtk2-engines-gtk-qt".

This will give the kde look to gnome windows.
Next to that, certain gtk applications are launched with kdesu, which means root profile.

After the gtk2-engines-gtk-qt is configured, what you can do is simply to copy youe kde profile to the gnome directory, and when rebooting, you will see that event sudoed applications will have the good look.

Copy your profile that way :

```
sudo cp -rf ~/.kde /root
```

I hope this will help ;)

---

### Post by ltmon on 2005-07-22
Firefox can be tweaked to look better in KDE, look for the CrystalFox theme on the Mozilla theme site.  It's still a hack though, it doesn't really integrate well at all.

Konq should be able to play embedded media through Kaffeine out of the box.  I've had mine work with embedded wmv, mpg without any extra configuring.

As far as plugins go, it's said that any plugin available to Firefox should also be available to konqueror.  If this I suggest you go to "Settings" -> "Configure Plugins" and click "Scan for New Plugins" and see if it helps.

Otherwise:
Java:
[http://www.konqueror.org/javahowto/](http://www.konqueror.org/javahowto/)

L.

---

