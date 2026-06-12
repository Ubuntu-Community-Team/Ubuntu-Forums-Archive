---
title: "can I stop auto mounting?"
date: 2009-03-02
forum: General Help
---

### Post by Arminius on 2009-03-02
every time I plug my iphone in ubuntu try's to auto mount it, but I want just my windows xp to mount it, so how do I tell ubuntu that only this iphone is not to be mounted?

---

### Post by InspiredIndividual on 2009-03-03
I don't have much expertise on this, so I may not be able to help you out if the following doesn't work for you. That being said, editing the automount settings of Nautilus will probably work. You can do so in the Gnome Configuration Editor:

```
 gconf-editor 
```

Click through the menu to apps > nautilus > preferences. Now, uncheck the "media_automount" option. Be aware this will influence the general behaviour. Thus, if you plug in, say, a usb-stick, it won't automount either. If you want to prevent automount on a per device basis, that's a bit trickier. It's probably necessary to edit fstab if you want to do so. A comprehensive guide to fstab can be found here: 
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Arminius on 2009-03-04
thank you InspiredIndividual you beautiful genius, that works perfectly now

---

### Post by InspiredIndividual on 2009-03-04
You're welcome! Glad to be able to help...

---

### Post by brolin on 2009-03-10
**InspiredIndividual:**  Your solution (appears to) Work(s) For Me™ too.  Incidentally, are you a Dell Inspiron user? ;)

**Arminius:** Please prepend "[solved]" to your original post's ... Title (is that the correct vBulletin term?).

---

### Post by InspiredIndividual on 2009-03-10
> **brolin said:**
> **InspiredIndividual:**  Your solution (appears to) Work(s) For Me™ too.  Incidentally, are you a Dell Inspiron user? ;)


No, I ordered a manually assembled system at a mail order firm that was recommended by a friend of mine. Anyway, nice to see it worked for you!

---

### Post by dcstar on 2009-03-10
> **InspiredIndividual said:**
> I don't have much expertise on this, so I may not be able to help you out if the following doesn't work for you. That being said, editing the automount settings of Nautilus will probably work. You can do so in the Gnome Configuration Editor:

```
 gconf-editor 
```

Click through the menu to apps > nautilus > preferences. Now, uncheck the "media_automount" option. Be aware this will influence the general behaviour.
........

Or **simply** open Nautilus-Edit-Preferences-Media and deselect "Browse media when inserted".

Most of these basic things are in the GUI, there is no need to stuff around with individual low-level key settings.

---

### Post by InspiredIndividual on 2009-03-11
Thanks dcstar, I didn't know that. I'll be sure to suggest your solution in the future.

---

