---
title: "Firefox autofill window type"
date: 2008-04-07
forum: Desktop Effects &amp; Customization
---

### Post by kss42 on 2008-04-07
This is a very minor problem, but it's annoying and hopefully there's a quick fix.
I'm running Hardy with Compiz effects enabled, and the default animations for window open/closing. The trouble is with the little drop-down autofill menus in Firefox - the ones that show up under form fields and the search/URL bars when you start typing. They are coming in with the "Glide" animation used for application windows, but I want them to use the "Fade" animation that drop-down menus should have. If I knew the name or specific type of these particular windows, I could use ccsm to adjust my settings. Does anyone know the window type for Firefox autofill menus?

---

### Post by FuturePilot on 2008-04-07
The latest Firefox update in Hardy seems to have broken something in the Compiz Workarounds plugin. So it's not really a Compiz problem but something with Firefox. I'm not sure what can be done about it. I have the same problem.

---

### Post by kss42 on 2008-04-07
Thank you. I guess that's what I get for using beta software. I will wait for the final 3.0 release before I complain again.

---

### Post by the yawner on 2008-04-07
I'm not sure how the workaround plugin affected this effect before, but I've tamed it somewhat by adding a new Open Animation rule.

Open Effect: Fade
Duration: 150
Window Matching: class=Firefox & override_redirect=1

---

