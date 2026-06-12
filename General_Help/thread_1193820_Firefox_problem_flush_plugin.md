---
title: "Firefox problem flush plugin"
date: 2009-06-21
forum: General Help
---

### Post by colau on 2009-06-21
HI,
Why are the flash contents not being loaded automatically?
[COLOR="Silver"]*At the top in attached image file*[/COLOR]

---

### Post by lovinglinux on 2009-06-22
Because you have the open source flash plug-in, which is not compatible with all sites. To solve this problem remove all flash plug-ins and install the one from Adobe. Open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree
```

Don't get me wrong, but it is [Flash](http://en.wikipedia.org/wiki/Adobe_Flash) [wikipedia.org] not Flush.

---

### Post by colau on 2009-06-22
> **lovinglinux said:**
> Because you have the open source flash plug-in, which is not compatible with all sites. To solve this problem remove all flash plug-ins and install the one from Adobe. Open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree
```

Don't get me wrong, but it is [Flash](http://en.wikipedia.org/wiki/Adobe_Flash) [wikipedia.org] not Flush.
Thanks.It worked.

---

### Post by isbiyanto on 2010-08-08
yes.... thanks

---

### Post by lovinglinux on 2010-08-08
For future reference, see [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by isbiyanto on 2010-08-11
yes.... thanks :KS:KS:KS

---

