---
title: "Iceweasel on 8.10"
date: 2009-01-31
forum: General Help
---

### Post by mashcaster on 2009-01-31
Where do I get the latest iceweasel deb from so I can install it on 8.10?

---

### Post by m_duck on 2009-01-31
[This]("http://packages.debian.org/lenny/iceweasel") is the link to the Iceweasel deb in the Debian Lenny repo's. I've not the foggiest if it will work in Ubuntu. You will need to scroll to the bottom and choose your architecture then choose a mirror to download the deb.

---

### Post by khelben1979 on 2009-01-31
I have experienced Iceweasel to be a bit unstable myself and I would suggest that you go for the Opera web browser also so you might get a better browsing experience or... at least, an alternative to the Firefox browser.

I'm on a Debian Lenny system over here and on the ppc architecture it has stopped working completely.
You can find the Opera web browser [here]("http://rpmfind.net/linux/rpm2html/search.php?query=opera&submit=Search+...") if you're interested.

I also suggest that you use the alien application to convert it to the more suitable DEB format. ( apt-get install alien )

---

### Post by man_bash on 2009-04-16
Thanks for the link m_duck!

Cannot even install Iceweasel though, it tries to overwrite /usr/bin/firefox/, which I'd like to keep if possible.

If you are looking for Opera, why not get the .deb from their website and not bother with alien?

---

### Post by khelben1979 on 2009-04-16
> **man_bash said:**
> If you are looking for Opera, why not get the .deb from their website and not bother with alien?

Good point. Getting it from the rpmfind.net might be a better idea though if your looking for an older version or if your looking for a package which supports another cpu architecture.

---

### Post by James_Lochhead on 2009-04-16
You can get debs of Opera from their website.

---

