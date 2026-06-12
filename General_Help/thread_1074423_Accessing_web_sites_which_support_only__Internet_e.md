---
title: "Accessing web sites which support only  Internet explorer"
date: 2009-02-19
forum: General Help
---

### Post by deepakbm on 2009-02-19
How can i access sites that supports only ie.
I tried installing wine but couldnt install ie 7.
Is there any other any other ways of accessing such sites?

---

### Post by x33a on 2009-02-19
you could try spoofing the user agent of the browser.

in firefox, download user agent switcher addon.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

in opera, right click a webpage and edit site preferences -> network -> browser identification.

---

### Post by deepakbm on 2009-02-19
Thanks

---

### Post by nothingspecial on 2009-02-19
> **deepakbm said:**
> 
I tried installing wine but couldnt install ie 7.


[[COLOR="Cyan"]You can, however install ie6[/COLOR]]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

---

### Post by mb_webguy on 2009-02-19
Spoofing the user agent only works for sites that check for and require IE, but don't use IE-specific technologies like ActiveX plugins, which are rare.  Generally, the reason they check for IE is because they *do* use ActiveX plugins.

The best way around this is to install [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") under Wine.

---

### Post by dcstar on 2009-02-19
> **mb_webguy said:**
> Spoofing the user agent only works for sites that check for and require IE, but don't use IE-specific technologies like ActiveX plugins, which are rare.  Generally, the reason they check for IE is because they *do* use ActiveX plugins.

The best way around this is to install [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") under Wine.

Or having a Windows installation running in a VM for these (all too common) circumstances.

That is basically the only reason I keep XP in my VMware Server VM list.

---

### Post by aryan10 on 2009-05-06
[FONT=Calibri]Hey folks...what do you guys think about the new IE8? Have heard a lot about it, but I’m still using Firefox! Just saw this video about their Crash recovery feature, guess it might be worth a try- [/FONT][[FONT=Arial]http://www.youtube.com/watch?v=nFTUqK-cOuE[/FONT]]("http://www.youtube.com/watch?v=nFTUqK-cOuE")_[COLOR=blue][FONT=Arial][/FONT][/COLOR]_

---

### Post by aspora.isernia on 2009-05-06
> **nothingspecial said:**
> [[COLOR="Cyan"]You can, however install ie6[/COLOR]]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

Great!! It worked like a charm!! Thanks

---

