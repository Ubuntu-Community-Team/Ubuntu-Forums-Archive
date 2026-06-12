---
title: "How do you make Gnome 3 the default desktop?"
date: 2011-10-31
forum: Desktop Environments
---

### Post by Mazate on 2011-10-31
An answer to this would be most appreciated.

---

### Post by MG&amp;TL on 2011-10-31
As in, the defult login? I personally just used it once, and it kept my choice for next time.

---

### Post by Frogs Hair on 2011-10-31
> **MG&TL said:**
> As in, the defult login? I personally just used it once, and it kept my choice for next time.

+1 Ubuntu defaults to whatever I used last .

---

### Post by Thorvaldsson on 2011-10-31
Assuming you have Gnome installed, you should be able to select it at log in.  After that, Ubuntu should remember your choice.

---

### Post by Mazate on 2011-10-31
> **Thorvaldsson said:**
> Assuming you have Gnome installed, you should be able to select it at log in.  After that, Ubuntu should remember your choice.


Well, I logged out of Unity, switched to Gnome 3 and then I was fine.  I turned off my computer for the day and turned it back on the next day and it loaded Unity again.

---

### Post by markbl on 2011-10-31
> **Mazate said:**
> Well, I logged out of Unity, switched to Gnome 3 and then I was fine.  I turned off my computer for the day and turned it back on the next day and it loaded Unity again.
This is a bug on launchpad but I think it has been fixed in very recent updates. Either way, you can run the following to force the default:
```

sudo /usr/lib/lightdm/lightdm-set-defaults --session gnome-shell

```

---

### Post by Azyx on 2011-10-31
Is <Gnome3 the same as Gnome-shell? Aren't Gnome shell a variant of Gnome3

---

### Post by MG&amp;TL on 2011-11-01
Gnome-shell is the default desktop for the gnome3 release. However, as demonstrated by Unity, it is perfectly possible to build different desktops out of gnome releases.

---

