---
title: "Newly Installed Programs Don't Appear in Menu"
date: 2006-01-15
forum: Desktop Environments
---

### Post by Paul Gilster on 2006-01-15
I had to reinstall Akregator because of a crash and although I can run it from the command line, KDE will not let me put it into the main KDE menu (and I had assumed it would show up there automatically in any case). When I use the menu editor, I make the needed addition, but the menu item does not show up even after a reboot. Any ideas? I'm running Breezy, and until now the menu editor worked fine, as did installing programs (which always appeared in the KDE menu afterwards).
Thanks! -- Paul

---

### Post by solarwind on 2006-01-15
try rebooting

that works almost all the time
 
if you prefer not to reboot, atleast restart X

---

### Post by Paul Gilster on 2006-01-15
Reboots don't work, I'm afraid; I've tried numerous times. Kmenuedit simply won't accept my editing, and any new programs I install via Adept (even when KDE apps), don't show up in the KDE main menu.

---

### Post by GeneralZod on 2006-01-16
Try running

```

kbuildsycoca

```

from the command-line. Also, run kmenuedit from the command-line, make your changes, and see if any errors are reported in the output.

---

### Post by Paul Gilster on 2006-01-16
Thanks to this forum, I found the answer:

sudo chown -R <username> /var/tmp/kdecache-<username>

I don't understand Ubuntu enough to know exactly what's happening, but somehow ownership of some of these files got changed, I think through using sudo within the KDE environment.

So now I'm perplexed. What's the fix to avoid this happening again -- avoid sudo within KDE, or use kdesu?

---

### Post by Rackerz on 2006-01-16
The sudo command isn't the problem here I don't think.

---

### Post by jacob_lurch on 2006-01-20
[QUOTE=Paul Gilster]Thanks to this forum, I found the answer:

sudo chown -R <username> /var/tmp/kdecache-<username>

[/QUOTE]

Well, this worked sweet for me.  Thanks.  I don't know why KDE and sudo seems to bork the ownership of some files.

---

