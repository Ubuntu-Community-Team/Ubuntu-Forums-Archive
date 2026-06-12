---
title: "Getting Blackjack back (on 12.04LTS)"
date: 2013-05-14
forum: Gaming &amp; Leisure
---

### Post by dvdhudson33 on 2013-05-14
I'm aware that gnome-games dropped Blackjack from its lineup back in '09, but I looove playing it when bored.

I tried lgdb.org, gamingonlinux.com, even Steam, but amazingly (for the world's second-most-popular IRL gard game) there's nothing around for Linux.

So, I found and downloaded a deb package of the old gnome-games version from [this page]("http://www.iheartubuntu.com/2010/11/no-more-blackjack-in-ubuntu.html").

Ubuntu Software Centre won't install it, as it's missing a dependency called 'gnome-games-common', which has apparently been superseded by gnome-games-data (which I have).   I searched around for gnome-games-common, to no avail.  Nor could I find anything on gnome's [helpforusers]("https://live.gnome.org/HelpForUsers") page (which is not surprising, since they dropped it long ago).  Nor can I find any mention, anywhere, of anyone else having had this issue.

So, does anyone know anything about how to 're-direct' a package's dependencies?  Or other suggestions?

If all else fails, I can get something for Windows and try it with Wine, but I'd like to stick to something Linux-native if I can.

Muchos gracias, folks.

---

### Post by ibjsb4 on 2013-05-14
Gnome-games-common was last built for Lucid (10.04).  This package is available [here]("http://packages.ubuntu.com/lucid/gnome-games-common").

Here's the strange part.  Even though its been dropped, all dependencies for this package appear to be in place for Precise (12.04).  So maybe you could download and install this package using the "dpkg -i" command without going through dependencies hell.  The big question is will you break anything else.

---

### Post by dvdhudson33 on 2013-05-15
> **ibjsb4 said:**
> The big question is will you break anything else.

Well as it happens, yes, all the other gnome games!  But nothing else.

Thanks so much for finding that link for me.  I now have Blackjack for when I'm pretending to be listening in lectures.  *pats ibjsb4 on back*

---

### Post by ibjsb4 on 2013-05-15
ibjsb4 takes pats on back and walks proudly off into sunset :)

---

