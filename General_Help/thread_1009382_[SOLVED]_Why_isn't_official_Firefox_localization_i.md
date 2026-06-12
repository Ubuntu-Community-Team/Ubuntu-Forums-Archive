---
title: "[SOLVED] Why isn't official Firefox localization included in Ibex and Hardy?"
date: 2008-12-12
forum: General Help
---

### Post by abcuser on 2008-12-12
Hi,
I can see my language localization is included in official Firefox 3.0.4 download page for Linux [http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

So I can download it and install it on Ubuntu 8.10. But I don't really want to do that because package manager on my Ubuntu will not know anything about this install, so potential problems can arrive - and I need stable system on this PC, because I make a bank transactions on it and I don't want to break operating system.

My question is why isn't translation included in Ubuntu Ibex, so when turning Ubuntu to my local language most of the products are translated in Ubuntu, but Firefox isn't why?
P.S. There is also Firefox 3.1 beta 2 translated: [http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html)
Regards

---

### Post by philinux on 2008-12-12
[http://ubuntuforums.org/showthread.php?t=212310](http://ubuntuforums.org/showthread.php?t=212310)

---

### Post by abcuser on 2008-12-12
philinux, this is really old tutorial... not recommended for newer Ubuntu.

I found out solution browsing the web:
1. Download appropriate xpi file for your language from web page [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.4/linux-i686/xpi/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0.4/linux-i686/xpi/)
Note: change version number (in my case 3.0.4) in URL if using any other version of Firefox.
2. In Firefox select File | Open File and select xpi file.
3. Click install button.
4. Restart Firefox
and local language is installed.

Regards

---

### Post by philinux on 2008-12-12
Yep but I checked that this preference is still available and it is. And it mentions getting an xpi file.

general.useragent.locale

Mines set to en-US so I assumed it would still be valid. :p

---

