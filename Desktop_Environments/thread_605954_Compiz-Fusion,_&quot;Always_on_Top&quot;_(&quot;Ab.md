---
title: "Compiz-Fusion, &quot;Always on Top&quot; (&quot;Above&quot; doesn't help)"
date: 2007-11-07
forum: Desktop Environments
---

### Post by paul.reloaded on 2007-11-07
Hello.
Does anybody know how to make windows in Compiz-Fusion "always on top" ?
I use pidgin and I have enabled Hotkeys plugin and it feature "Toggle list". So when I press some shortcut Pidgin appeared above other windows before (when I had metacity). But in Compiz-Fusion it doesn't. So I tried to put "name=pidgin" to "Above" option in "Window Rules" of CCSM, but now It just opens above other windows, but not above current opened window.

---

### Post by franke on 2008-05-25
Big Bump on this one!

I have exactly the same problem and this is keeping me from turning animations on. Stuck with Metacity :(.

---

### Post by prshah on 2008-05-26
> **paul.reloaded said:**
>  So I tried to put "name=pidgin" to "Above" option in "Window Rules" of CCSM, but now It just opens above other windows, but not above current opened window.
> **franke said:**
> Big Bump on this one!
I have exactly the same problem and this is keeping me from turning animations on. Stuck with Metacity :(.

Instead of putting name=pidgin, try ```
title=Buddy List
``` in the same "Above" box of Window Rules in CCSM. I think you also need to enable the "Always on top" option by right-clicking pidgin's title bar and choosing "Always on top".

---

### Post by franke on 2008-05-28
The setting in CCSM looks now like this: (title=Buddy List) & name=pidgin
I have also clicked "always on top" in the Pidgin window.

It still doesn't come on top, say while I have Firefox open.

---

### Post by Gregormo on 2008-07-14
I just had the same problem. You've got to go to General Options > Focus & Raise Behavior and set "Focus Prevention Level" to "off". This is the only option you need to get Pidgin on top when hitting the hotkeys.

---

### Post by franke on 2008-07-15
> **Gregormo said:**
> I just had the same problem. You've got to go to General Options > Focus & Raise Behavior and set "Focus Prevention Level" to "off". This is the only option you need to get Pidgin on top when hitting the hotkeys.


Thank you! Feels so good getting this solved :).

---

