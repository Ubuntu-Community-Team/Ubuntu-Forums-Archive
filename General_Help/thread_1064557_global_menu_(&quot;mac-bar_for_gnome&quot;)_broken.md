---
title: "global menu (&quot;mac-bar for gnome&quot;) broken: help appreciated"
date: 2009-02-08
forum: General Help
---

### Post by manualqr on 2009-02-08
I just compiled Vala 0.5.5, and used it to build the revision 2259 of global menu. The build went well, and I can add the applet to my panel.

The problem is that the preferences menu is blank (just a blank maybe 40x40 pixel window) with nothing in it (I resized it to check). Of course, the global menu functionality is not there at all as I can't see it on the panel.

The only reason I built it all from source is that I had the EXACT same problem with the stable build in the PPA.

Any help/solutions?


note:
I will file a bug report if there isn't an immediate solution to the issue. I've already posted on their [wiki]("http://code.google.com/p/gnome2-globalmenu/wiki/BuildFromSourceOnUbuntu").

---

### Post by manualqr on 2009-02-09
No replies?
Any suggestions, alternatives, fixes?

thank you for your time!

---

### Post by k3ttc4r on 2009-02-10
well, as far as i remember, i used a .deb link i got out of the comments on their installation page, which would be this one:

>  Comment by Cassidy.James.Blaede,  Jan 15, 2009

Here's a link to a .deb for Ubuntu Intrepid! I converted it from the Fedora package and it seems to work just fine!

[http://sites.google.com/site/cajablatech/various-ubuntu-files/gnome-globalmenu_0.7.1-1.fc10_i386.deb](http://sites.google.com/site/cajablatech/various-ubuntu-files/gnome-globalmenu_0.7.1-1.fc10_i386.deb)


and everything works fine.. and afaik the settings window is supposed to be empty - it's not a final release yet, after all, so not everything's done yet.

---

### Post by grturner on 2009-02-14
[http://code.google.com/p/gnome2-globalmenu/issues/detail?id=326](http://code.google.com/p/gnome2-globalmenu/issues/detail?id=326)

```
sudo cp /usr/etc/gconf/schemas/gnome-globalmenu.schemas /etc/gconf/schemas

```
```
gconftool --install-schema-file /etc/gconf/schemas/gnome-globalmenu.schemas
```

log out and log back in

---

