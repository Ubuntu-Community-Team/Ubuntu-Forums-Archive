---
title: "Vanashing GPanel contents"
date: 2006-11-03
forum: Desktop Environments
---

### Post by ivanwillsau on 2006-11-03
I lock my computer every night before going home, but since I have upgraded to Edgy when I log back on in the morning all of the menus, icons, running program icons and desktop switcher have vanished. The only things that don't vanish are GAIM running icon, the dictionary, volume control and note taker applets, which are all, as I understand, separate programs.

Anyone have any ideas on how to fix this with out logging out and back in again?

Thanks
Ivan

---

### Post by boban on 2006-11-03
Can you open up "run application" (alt+f2)? If so, try:

```

killall gnome-panel && gnome-panel

```

If you cannot open it try opening terminal, run command mentioned above, then run "run application", kill terminal and run this command again (wired solution, but it worked for me when my panels vanished on dapper) :)

---

### Post by ivanwillsau on 2006-11-03
Thanks, that work. Any ideas on why it happens?

Ivan

---

### Post by boban on 2006-11-03
In Edgy - it happens sometime because of Xgl and/or ati drivers... But in dapper it happened to me without any apparent reason (but I remember that after installing Xgl it happened more often)...

---

