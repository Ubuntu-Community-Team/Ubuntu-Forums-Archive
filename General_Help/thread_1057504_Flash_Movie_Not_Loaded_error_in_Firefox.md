---
title: "Flash Movie Not Loaded error in Firefox"
date: 2009-02-01
forum: General Help
---

### Post by dbbolton on 2009-02-01
I'm using Xubuntu Intrepid 64bit, and I have the nonfree version of the Adobe flash plugin. about:plugins lists "Shockwave Flash 10.0 r15". 

It seems that sporadically some flash movies will not load. For example, youtube videos will show up as a black area on the page. Right-clicking on them will show a context menu with "Movie not loaded" and "About Adobe Flash". However, youtube videos appear to play fine in Epiphany (gecko).

Any thoughts?

---

### Post by tuxxy on 2009-02-01
Yes you will experience issues using the flashplugin-nonfree available in the repos.  The reason for this is thats the 32-bit plugin, which has use another file to enable it run on your 64-bit system.

This is down to Adobe not releasing plugins for 64-bit platforms but you are in luck as they recently released a native 64-bit plugin which runs excellent, heres my other thread of where to download and how to install and be sure to remove the flashplugin-nonfree from synaptic first.

[http://ubuntuforums.org/showthread.php?t=999313](http://ubuntuforums.org/showthread.php?t=999313)

Just download the plugin extract to desktop and copy it to your /usr/lib/mozilla/plugins dir :)

---

### Post by dbbolton on 2009-02-01
> **tuxxy said:**
> Yes you will experience issues using the flashplugin-nonfree available in the repos.  The reason for this is thats the 32-bit plugin, which has use another file to enable it run on your 64-bit system.

This is down to Adobe not releasing plugins for 64-bit platforms but you are in luck as they recently released a native 64-bit plugin which runs excellent, heres my other thread of where to download and how to install and be sure to remove the flashplugin-nonfree from synaptic first.

[http://ubuntuforums.org/showthread.php?t=999313](http://ubuntuforums.org/showthread.php?t=999313)

Just download the plugin extract to desktop and copy it to your /usr/lib/mozilla/plugins dir :)
Thanks

---

### Post by dbbolton on 2009-02-01
Also, will I need to put the .so file any where else so that Epiphany can utilize it?

---

### Post by tuxxy on 2009-02-01
No it will be fine, epiphany should use that dir for plugins also.

If not you would put it in /usr/lib/epiphany/plugins but am sure you wont need to.

---

### Post by dbbolton on 2009-02-02
At first it was working, but now I'm getting the same error as before :/

---

