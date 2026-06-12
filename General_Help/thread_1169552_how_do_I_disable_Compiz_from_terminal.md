---
title: "how do I disable Compiz from terminal?"
date: 2009-05-25
forum: General Help
---

### Post by aidanb on 2009-05-25
I turned on a few too many "features" in Compiz, which made the screen go black in random rectangles, rendering it useless. The problem is, it turns on these features automatically when I log in, so I can't use the GUI to turn it off. I know how to start a session as just a terminal, but how do I turn Compiz off or switch to basic version with no decorations, etc using the cli? I tried deleting files from ~/.gconf and from /usr/lib/compizconfig but the problem remained.

---

### Post by kpkeerthi on 2009-05-25
Press ALT + F2 and enter
```
metacity --replace
```

---

### Post by aidanb on 2009-05-25
Thanks, that did it! I'll be sure to remember that. I really appreciate your help!
 
(an aside: I like the fact that Compiz has "ADD Helper" under Accessibility. Maybe I should try it. lol )

---

### Post by kpkeerthi on 2009-05-25
Install compizconfig-settings-manager using Applications -> Add/Remove. It has an option to restore everything to defaults.

To turn off compiz completely, System -> Preferences -> Appearance -> Visual Effects -> None.

---

### Post by Jersey Legend on 2009-06-15
finally.  I've been looking for a long time now how stop all these effects.  I don't know how they became enabled.  One day they just did after a restart. The option to take them off doesnt appear.  Im using a mini right now and browsing has become smoooother

---

