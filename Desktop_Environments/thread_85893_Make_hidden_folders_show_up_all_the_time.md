---
title: "Make hidden folders show up all the time"
date: 2005-11-03
forum: Desktop Environments
---

### Post by BLTicklemonster on 2005-11-03
I want my .wine folder to be visible at all time, no matter how I browse for it. 


How can I do this? Clicking view hidden folders only works while a particular browser is open. Once closed they are hidden again.

---

### Post by jasay on 2005-11-03
To show all hidden files/folder all the time: In nautilus Edit >  Preferences, click show hidden and backup files (under Default view).

Does anyone know if there is a way to make this setting folder specific?  E.g. Can I make it so I can see hidden files in my home directory, but not elsewhere?

---

### Post by trilo on 2005-11-03
Hi :)

More info would make helping you easier but I'll assume you're using nautilus to browse your folders. There's a very good manual for nautilus (click on 'Help', doh) which will show you many things, one of which is the 'preferences' dialog, wherein you'll find a tick box for 'show hidden folders'.

---

### Post by SilentCacophony on 2005-11-03
If you're looking for a solution for nautilus, Edit->Preferences, then tick the 'Show hidden and backup files (in the 'View' tab.)

On the commandline, you can use **ls -a**, or **ls -la**. The -a is the pertinent option there.

> Does anyone know if there is a way to make this setting folder specific? E.g. Can I make it so I can see hidden files in my home directory, but not elsewhere?

Not that I know of. I'm thinking rox-filer may do that with the right configuration, but not sure.

---

### Post by sethmahoney on 2005-11-03
You can always create shortcuts to those hidden folders you want to stay visible all the time.

---

### Post by BLTicklemonster on 2005-11-03
Ah yes, thanks. I was just clicking it in "view" and it kept going away. Now I can see my .wine and .loki and all that. I appreciate your timely replies.

Now is there a way to make stuff I copy stay in the "clipboard" (for lack of a better word) even if I close the item I copied from so I can paste? At present, if I copy something while in gedit, and want to paste it in something else, and gedit closes, I lose what I had copied.

---

