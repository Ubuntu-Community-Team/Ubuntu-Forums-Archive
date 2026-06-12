---
title: "Urxvt loses controls with tabbed extension enabled"
date: 2009-03-04
forum: General Help
---

### Post by Yashiro on 2009-03-04
Under Compiz (and perhaps other window managers) using the tabbed perl extension for Urxvt results in the user losing their window controls. User cannot drag, close, minimize the current terminal window.

This is probably a bug within Urxvt but can be fixed by doing the following.

Find the perl extension:
$PREFIX/lib/urxvt/perl/tabbed  

Comment out(#) or delete this line:
```
$self->XDeleteProperty ($self->parent, $_) for keys %our_props;
```

Save and relaunch Urxvt -pe tabbed. Should be fixed.

---

