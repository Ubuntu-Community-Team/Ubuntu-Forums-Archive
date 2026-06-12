---
title: "Remove minimaze boarders in gnome"
date: 2008-02-25
forum: Desktop Environments
---

### Post by dmsn on 2008-02-25
Hello 
I use gnome and i have visual effect "none" and i really dont like when i minimaze programs exempel
the terminal. Its ugly black boarders, ist possible to delete them ? I dont want to run compiz/beryl.
LIke in Xfce4 it works good but i prefer gnome.
Thanks for help.

---

### Post by deepclutch on 2008-02-25
if u dont want compiz,press alt+f2 and inside run "metacity --replace"

---

### Post by firefeather on 2008-02-25
If you're using Ubuntu 7.10 ("Gutsy"), go to System -> Preferences -> Appearance, click on the "Visual Effects" tab, and click "None". The "metacity --replace" will only temporarily solve your problem.

---

### Post by dmsn on 2008-02-25
I already run NONE in visual effect i wrote that aswell.

---

### Post by kaos_frack on 2008-02-25
Do you mean the wireframe effect?
I hate that as well, so here's what I did:
```

1. Type Alt-F2 > type "gconf-editor" > go to "apps/metacity/general" > enable "reduced_resources"
2. Go to "System > Preferences" > enable "Enable assistive technologies"

```

---

### Post by dmsn on 2008-02-25
kaos_frack: Thank you so much, i love you :)

---

### Post by firefeather on 2008-02-26
I'm sorry, I had a hard time understanding you. Please forgive me.

> **dmsn said:**
> I already run NONE in visual effect i wrote that aswell.

---

