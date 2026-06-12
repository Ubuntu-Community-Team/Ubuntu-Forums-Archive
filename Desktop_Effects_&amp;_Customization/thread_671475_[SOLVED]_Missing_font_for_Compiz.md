---
title: "[SOLVED] Missing font for Compiz?"
date: 2008-01-18
forum: Desktop Effects &amp; Customization
---

### Post by phyrewall on 2008-01-18
I've tried searching for a solution, but it's hard to describe...

See attachment for a pic of what's happening. It's like a font is missing. Any ideas?

---

### Post by luisromangz on 2008-01-19
Have you enabled the Text plugin?

---

### Post by phyrewall on 2008-01-21
> **luisromangz said:**
> Have you enabled the Text plugin?

Yes. Apparently that wasn't the problem. It seems to have been solved by running:

```
sudo dpkg-reconfigure fontconfig-config
```

and/or

```
sudo dpkg-reconfigure fontconfig
```

Thanks for the assist.

---

