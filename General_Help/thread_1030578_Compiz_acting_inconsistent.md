---
title: "Compiz acting inconsistent"
date: 2009-01-04
forum: General Help
---

### Post by Andy06 on 2009-01-04
I was setting up desktop effects on an otherwise faultless installation (wireless working out of the box - it's that fault less) but it keeps behaving buggy. Things/effects are inadvertently initiated when they do not even have the enable checkbox ticked. Keys to initiate certain effects do not necessary do so and lastly, quite often desktop effects get disabled all on their own. There restore and export function isn't working so well since restored settings do not behave the way they are configured even if the right checkboxes are ticked.

Any Ideas?

Thanks

---

### Post by gettinoriginal on 2009-01-04
This will set compiz back to total default settings, then as you adjust something, check to see if the irratic behavior returns so you know which setting it might be.  :P
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by Andy06 on 2009-01-04
Thanks I followed your advice.

In the opacity, brightness and saturation plugin, I created a filter to open all normal and dialog boxes on 90% opacity. Then I configured firefox to open at 100% opacity. I think these 2 conflict as firefox is also a normal window. Why this takes down the whole of compiz is beyond me. Also desktop effects are randomly disabled even without this (perhaps when memory requirements are too high? Because it always happens when I execute something new).

Thanks

---

### Post by gettinoriginal on 2009-01-04
Are you running emerald as the window decorator, I am, and am having no difficulties.  Just a suggestion.  :P  But if you consider this resolved, then please go to tools and mark the thread solved.  thank you

---

### Post by Andy06 on 2009-01-05
Nope not emerald, just the default one.

---

### Post by gettinoriginal on 2009-01-05
Just a suggestion, Install Emerald and Compiz Fusion Icon, that way you have better control over your window decorator and window manager.  :P

---

