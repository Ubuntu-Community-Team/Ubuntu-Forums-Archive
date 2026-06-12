---
title: "Firefox javascript errors (XUL) very annoying."
date: 2005-10-18
forum: Desktop Environments
---

### Post by nehalem on 2005-10-18
Every time javascript is invoked I get this error:

> Error: uncaught exception: [Exception... "Component returned failure code: 0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS) [nsIXPCComponents.lookupMethod]"  nsresult: "0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS)"  location: "JS frame :: chrome://global/content/XPCNativeWrapper.js :: anonymous :: line 91"  data: no]

It's really, really annoying since I use that javascript console for debugging my web pages (which is my occupation).  This is a big problem for me as it also seems slow things down.  Any ideas???

---

### Post by HermanAB on 2005-10-18
I guess the only solution is to avoid use of a Mozilla engined browser.  The KDE javascript engine seems to be far more robust than Mozilla's Spidermonkey, so try Konqueror or Opera.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by nehalem on 2005-10-18
That's not an option.  As a web programmer I target mozilla and IE.  So I need to ensure that firefox works.  Man, mostly breezy is nice but I must say I have had some wierd issues...

---

### Post by Cred on 2005-11-06
[QUOTE=nehalem]It's really, really annoying since I use that javascript console for debugging my web pages (which is my occupation).  This is a big problem for me as it also seems slow things down.  Any ideas???[/QUOTE]
I have the very same problem. With Hoary there was no problems, when Breezy came out I did a fresh install. First at work to an older computer and when I saw Ff beeing slow with Google maps for example I just told my self it's the RAM or something. Now at home I have the very same problem. Either it's something on the Breezy configuration or in the Ff package since the same version (and even older) Ff on Windows XP works smoothly and without problems :(

---

### Post by garak on 2005-11-17
There was the same problem with Hoary and Firefox 1.0.6 (see [this thread]("http://ubuntuforums.org/showthread.php?t=57481"))
It disappeared with upgrade to Firefox 1.0.7
But with Breezy (and FF 1.0.7 of course) it's here again :(

---

