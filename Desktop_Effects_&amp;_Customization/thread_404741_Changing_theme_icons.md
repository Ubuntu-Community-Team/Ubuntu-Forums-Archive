---
title: "Changing theme icons"
date: 2007-04-08
forum: Desktop Effects &amp; Customization
---

### Post by Keiji on 2007-04-08
When I try to replace the icons in /usr/share/icons/, nothing happens... even though I replace all sizes including the SVG. Is there a cache somewhere which needs to be refreshed, and if so how do I do that?

I want to change the icons because 1. IMO they look very inconsistent within programs (e.g. the stop button is huge compared to the back and forward buttons) and 2. Some of them just look plain bad (the cancel icon certainly rings a bell here) and I have made better ones.

---

### Post by jlk on 2007-04-09
Yes there is an Icon cache file icon-theme.cache for each theme.   To update the cache after  changing an icon use:

```
sudo gtk-update-icon-cache –force /usr/share/icons/Human
```

Replace **Human** with **the Theme you are using**.

---

### Post by Keiji on 2007-04-09
Thanks! That works great! Now that I know that, I'm surprised at how easy it is to change the icons across all applications at the same time. :)

---

