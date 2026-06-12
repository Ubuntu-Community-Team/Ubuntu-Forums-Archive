---
title: "Double-click in Firefox address bar to select part of URL"
date: 2008-12-03
forum: General Help
---

### Post by youknowho on 2008-12-03
I've read other posts on this topic and tried the solution mentioned, which is to go to about:config and set "layout.word_select.stop_at_punctuation" to true. 

It was true by default and turning it off/on didn't change double-click behavior in the address bar.

Like Firefox in Windows, I want to be able to double-click the URL in the address bar and select an individual word instead of the whole URL. So double-clicking on the "google" in "http://www.google.com" would highlight just "google". 

Are there any other solutions for this?

---

### Post by Tamlynmac on 2008-12-03
about:config

Search for:
browser.urlbar.doubleClickSelectsAll

If this value is set to true - change it to false.

---

### Post by Tamlynmac on 2008-12-04
Did this solve your problem? Have you not had an opportunity to apply the change?

---

### Post by youknowho on 2008-12-06
Yes that fixed it! Thank you very much! 

I had some additional options that I had changed from default in trying to get this to work, but once I set everything back to default (namely setting layout.word_select.stop_at_punctuation back to true) and changed browser.urlbar.doubleClickSelectsAll from its default true to false this worked. Thanks again.

---

