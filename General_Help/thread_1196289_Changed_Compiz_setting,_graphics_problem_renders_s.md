---
title: "Changed Compiz setting, graphics problem renders system unusable"
date: 2009-06-24
forum: General Help
---

### Post by IsaacClarke on 2009-06-24
I went to Compiz settings manager and enabled Blur Windows. After that, black bars obscured the top and bottom of my screen. I cannot click anything. Already tried the auto graphics fix in recovery mode. I'm using Jaunty, installed with Wubi on a Presario V3000.

Can provide specs if needed.

---

### Post by sedawk on 2009-06-24
Can you still open a terminal (e.g. by pressing ALT-F1, or ALT-F2, or ...
I can't test the correct combination currently, no combo seems to work.
But try to start "gnome-terminal").

In the terminal you can try to temporarily disable compiz with
```

nohup metacity --replace &

``` 

The desktop should get back to normal and you might be able to
undo your changes.

---

### Post by IsaacClarke on 2009-06-24
> **sedawk said:**
> Can you still open a terminal (e.g. by pressing ALT-F1, or ALT-F2, or ...
I can't test the correct combination currently, no combo seems to work.
But try to start "gnome-terminal").

In the terminal you can try to temporarily disable compiz with
```

nohup metacity --replace &

```The desktop should get back to normal and you might be able to
undo your changes.

Yes, I can start the terminal with CTRL-ALT F2. Will try this.

---

### Post by IsaacClarke on 2009-06-24
Tried this. It just gives me nohup: ignoring input and appending output to 'nohup.out'.

---

### Post by IsaacClarke on 2009-06-26
Bump.

---

### Post by VCoolio on 2009-06-26
This will reset ALL your compiz settings:
```
gconftool-2 --recursive-unset /apps/compiz
```

You can backup your compiz settings somewhere in ccsm, so once you have a decent setup do that, so you won't have to tweak everything again if something like this happens again.

---

### Post by IsaacClarke on 2009-06-26
> **VCoolio said:**
> This will reset ALL your compiz settings:
```
gconftool-2 --recursive-unset /apps/compiz
```You can backup your compiz settings somewhere in ccsm, so once you have a decent setup do that, so you won't have to tweak everything again if something like this happens again.

This worked. Everything's fine now.

Thanks.

---

