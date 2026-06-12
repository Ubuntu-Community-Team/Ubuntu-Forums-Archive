---
title: "Firefox 1.0.7 view source don't work"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Philippe Worontzoff on 2005-10-15
Hi,

When I want to view the source of a page with firefox, it is empty (and when I make a print preview of the source, the title is "about:blank").

I went into Most Frequently Reported Bugs for Firefox and I didn't saw that bug, so, I suppose the problem is on the Ubuntu 5.10 package of  Firefox 1.0.7.

Can someone help ?

---

### Post by khc on 2005-10-15
Does it happen with just one page, or every page?

---

### Post by Philippe Worontzoff on 2005-10-15
Every page.

Don't you have the same problem ?

---

### Post by bionnaki on 2005-10-15
page source works for me.

---

### Post by Philippe Worontzoff on 2005-10-15
Strange...

Here are the firefox packages installed for me :

firefox
firefox-gnome-support
mozilla-firefox-locale-en-gb
mozilla-firefox-locale-fr-fr

I've just installed "mozilla-firefox", but it doesn't change anything.

---

### Post by r@mix on 2005-10-15
Ctrl+U doesn't work but but the menu View/Source is ok. Strange.

---

### Post by Philippe Worontzoff on 2005-10-15
Ok, I know what's wrong, I used the extention [Html Validator]("https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&category=Developer%20Tools&numpg=10&id=249") and it doesn't work with Firefox 1.0.7 !

ctrl + u works for me, but, it seems that the ctrl + some keys don't work prety well, but that's offtopic.

---

### Post by r@mix on 2005-10-15
[QUOTE=r@mix]Ctrl+U doesn't work but but the menu View/Source is ok. Strange.[/QUOTE]
I correct myself : that was after installing/unistalling an extension (Grease Monkey). Now, after a reboot, the source viewing works fine with Ctrl+U, as with the menu.

---

