---
title: "[SOLVED] Ugly Open Office UI in Xubuntu"
date: 2007-04-03
forum: Desktop Environments
---

### Post by FuturePilot on 2007-04-03
This is weird. Why does Open Office look so ugly in the XFCE desktop? It's like there is no theme applied. And I thought Edgy had Open Office 2.1 not 2.0.?

---

### Post by kerry_s on 2007-04-03
Looks normal to me, i'm using feisty-custom-fluxbox install.

---

### Post by FuturePilot on 2007-04-03
So that is normal? I know in KDE and Gnome it has better integration with whatever KDE or GTK theme you're using.

---

### Post by marsmissionaries on 2007-04-03
uhm...looks like mine in gnome.

---

### Post by FuturePilot on 2007-04-03
See, here's a shot from my other computer using Gnome. It's much more integrated.

---

### Post by kerry_s on 2007-04-04
I think, not sure, but you might try installing> openoffice.org-gtk
I don't have gnome anything so i can't test it.

---

### Post by FuturePilot on 2007-04-04
Ah yes. Thanks! That worked. It looks much much better now:)

---

### Post by urukrama on 2007-04-05
I have the same problem runing Openbox. I have openoffice.org-gtk installed (and just updated), but it still appears ugly. Any idea how to overcome it?

Edit: Solved the problem. I  had to add ```
OOO_FORCE_DESKTOP=gnome
``` to my startup file. All looks nice now.

---

### Post by kpkeerthi on 2007-04-05
> **urukrama said:**
> I have the same problem runing Openbox. I have openoffice.org-gtk installed (and just updated), but it still appears ugly. Any idea how to overcome it?

Edit: Solved the problem. I  had to add ```
OOO_FORCE_DESKTOP=gnome
``` to my startup file. All looks nice now.

I have the same issue.. Can you please be specific as to which file and where you added that line?

---

### Post by Onyros on 2007-04-06
Just to add that in Fluxbox you have to add

```
export OOO_FORCE_DESKTOP=gnome
```

to the .fluxbox/startup file to get the same result :)

In Openbox I suppose it's the .openbox/startup file, without "export", though.

---

### Post by itsjustarumour on 2007-05-12
> **FuturePilot said:**
> See, here's a shot from my other computer using Gnome. It's much more integrated.

I had this same problem with OpenOffice Writer looking "ugly" - same as in your original screenshot.  Turns out it was just set to use what it described as "Default" icons - I changed this in the Writer settings to "Human" and - voila!  Looked just like it does in your second screenshot  :-)

I'm at work at the moment so I can only go by (rather rusty) memory, but I think the icons setting was under the main "Tools" menu, down to the bottom (one of the last two settings - "Preferences" or "Options" or something like that) and then the third sub-section down in the list there...

---

### Post by urukrama on 2007-10-11
I'm still having some difficulty with this. In pure Openbox, when I add the "export OOO_FORCE etc" to my autostart file all works well, but when I run Openbox within XFCE, I can't get it to work, as Openbox doesn't use the autostart file then. Adding an entry to the XFCE autostarted applications (under 'Settings') with that code in it doesn't work either. I have the openoffice.org-gtk installed.

Where could I add that line of code manually so that OpenOffice displays nicely in XFCE with Openbox?

---

### Post by jviscosi on 2007-10-12
I handled this in fluxbox/openbox by launching OO from small scripts rather than launching the programs directly.  Probably not the most elegant solution, but it works for me.  Here's an example script for launching writer:

```

[B] [jviscosi@VienneseWaltz ~/.scripts]
(6) $cat oowriter.sh[/B]
#!/bin/bash
export OOO_FORCE_DESKTOP=gnome
cd ~

oowriter "$@"

```

---

### Post by urukrama on 2007-12-30
I just solved this problem in a different way. If you have the openoffice.org-gtk package installed, you can launch it with the following command (for OpenOffice writer)

> openoffice --widgets-set gtk -writer

---

### Post by TinkerJ on 2008-01-21
Like you guys, I had the default ugly widget look in OO.org Writer. I figured I was missing a GTK+ library or something, and as mentioned, I installed openoffice.org-gtk along with openoffice.org-style-human.

At first it didn't work, probably because I had messed with the Options dialog too much. So I just deleted the ~/.openoffice.org2/ folder and restarted, and the icons appeared. You can install more openoffice.org-style themes and select them in "Tools->Options->View->Icon Size and Style"

---

