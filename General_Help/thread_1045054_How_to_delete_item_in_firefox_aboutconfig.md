---
title: "How to delete item in firefox about:config"
date: 2009-01-20
forum: General Help
---

### Post by afeasfaerw23231233 on 2009-01-20
I recently added an entry "nglayout.initialpaint.delay" in firefox about:config. Now how can I delete it? Thanks

---

### Post by rmills on 2009-01-20
Close firefox.  Locate the prefs.js file in your firefox profile directory.  It's in ~/.mozilla/firefox/<something_weird>.  The something_weird is "ekg3eh3w.default" for me.  Back up the prefs.js.  Open the original and remove the entry.  Open firefox.  It should be gone then.

---

### Post by x33a on 2009-01-20
go to about:config, enter nglayout.initialpaint.delay in the search area. right click on it and click reset. restart firefox, and it's gone.

---

### Post by afeasfaerw23231233 on 2009-01-20
Thanks! It works.

---

