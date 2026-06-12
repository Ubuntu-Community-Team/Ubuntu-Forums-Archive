---
title: "wolfenstein et not in full screen"
date: 2006-11-07
forum: Gaming &amp; Leisure
---

### Post by repins on 2006-11-07
Hey, i have been searching the forums to see if anyone else was having the same problem as me, so its probly just something sill on my behalf, but any help would be great. Ok i install wolfenstein ET just fine, but it will not play in full screen, although the settings from within wolf is set to full screen and resoulotion 1024x768. And i can always see my taskbar and work spaces.... Any help?

---

### Post by K.Mandla on 2006-11-08
(I've moved this to the gaming forum, where it should get more attention. ;) )

---

### Post by GazaM on 2006-11-08
Are you using Compiz or Beryl (not completely sure if it matters whether you're using XGL or AIGLX though) ? If you are, then there's your problem right there. It's a known issue, and there are some complicated workarounds.

Just switching back to metacity from Beryl doesn't help for me either whilst in XGL, it seems I have to be on a normal Xserver (ATI X700Pro here, using fglrx).

---

### Post by repins on 2006-11-10
> **GazaM said:**
> Are you using Compiz or Beryl (not completely sure if it matters whether you're using XGL or AIGLX though) ? If you are, then there's your problem right there. It's a known issue, and there are some complicated workarounds.

Just switching back to metacity from Beryl doesn't help for me either whilst in XGL, it seems I have to be on a normal Xserver (ATI X700Pro here, using fglrx).

Yes i am using beryl, and when i switch back to metacity still doesnt change anything also... I was pretty sure i had it running on this fine before.

---

### Post by maddog39 on 2007-02-05
I am using Beryl in a seperate session, but now when I login to the untouched GNOME session, it still does it, wolfenstein just wont maximize. What the heck! Does anyone have a fix?

---

### Post by chavo on 2007-02-05
I just use a separate X session - write a script like this .
```

#!/bin/bash
startx -- :1 -br
et

```

Just name it xet or something, mark it executable and put it in your ~/bin folder. Then hit Ctrl-Alt-F1, log in and run xet. Hit Ctrl-Alt-F7 and Ctrl-Alt-F9 to switch back and forth between et and your desktop. I usually log out of KDE anyway when I'm playing et, just to free up as many resources as possible.

---

