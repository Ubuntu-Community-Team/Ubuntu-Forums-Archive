---
title: "Firefox 3.0 display issue and Firefox 3.1 install"
date: 2009-01-17
forum: Desktop Environments
---

### Post by mansonthomas on 2009-01-17
Hi,

  I'm currently working with Firefox 3.0, and radio button, button select are incorectly displayed (partially draw, surronded with an ugly grey background).

 I've tryed to apply the fix in System Settings->Appearance->GTK Styles & Fonts-> Scrollbars fix, without success.

Also, I'm working a web application that work only under Firefox. I need to test it against Firefox 3.1. How Can I install a new version of Firefox 3.1 without touching the 3.0 already installed ? 

Thx,
Thomas.

---

### Post by taurus on 2009-01-17
You can basically download the new version.  Then, unpack it in your $HOME and run it from there.

---

### Post by adamlau on 2009-01-17
Download Firefiox release versions from here: [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/) and after decompression, run:

```
/path/to/firefox --ProfileManager
```

Reference the new profile a name different than your existing ~/.mozilla/firefox/profile.name and your current profile will not be touched.

---

