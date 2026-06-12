---
title: "How can i reset all keybindings in Compiz Fusion?"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by pjones0404 on 2007-07-07
i have made a few changes to the key bindings in fusion. there are a few that i do not like now. i go back into the settings manager and attempt to reset but it does not save the changes when i reset it back to default. it allows me to make the change but when i exit out and come back it was not changed.

is there a way to reset all key bindings so i can start over from the default settings?

---

### Post by hyperair on 2007-07-08
In your CompizConfig Settings Manager, change the backend to flat-file backend if it isn't already. Then open a terminal, and run this command:
```

rm ~/.compizconfig/*.ini

```

Then restart Compiz.
```

compiz --replace -c emerald

```

---

### Post by pjones0404 on 2007-07-09
that worked great.

thanks alot.

---

### Post by alacrityit on 2007-12-21
That directory didn't exist on my Gutsy install, but if you open up ccsm and go to the preferences section there's a "Reset to defaults" button that worked like a charm.

---

### Post by multisimple on 2008-06-26
```
gconftool-2 --recursive-unset /apps/compiz
```

if it doesnt work set your appearance preferences to normal then try the command

---

