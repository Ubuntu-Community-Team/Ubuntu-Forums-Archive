---
title: "[SOLVED] Changing the xkill cursor"
date: 2008-05-27
forum: Desktop Environments
---

### Post by Paul Miller on 2008-05-27
I've searched all over the forums and the intertubes, and I haven't been able to find the answer to this question.  My current xkill cursor is a boring "X" and I'd like it to be the default skull and crossbones.  How do I change it back?

Thanks!

---

### Post by sdennie on 2008-05-27
Sometimes the tubes can get full and it takes a while for the internets to reach you (it's not a dumptruck you know...):

```

sudo chmod -r /usr/share/icons/DMZ-White/cursors/pirate

```

If you notice any detrimental effects (I can't imagine you would), run the same command with "+r" instead of "-r".  This assumes you are using the default cursor theme.

---

### Post by Paul Miller on 2008-05-27
Awesomeness.  That fixed it.  Thanks much!

---

