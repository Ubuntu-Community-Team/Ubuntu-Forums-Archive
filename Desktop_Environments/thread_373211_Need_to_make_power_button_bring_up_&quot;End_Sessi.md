---
title: "Need to make power button bring up &quot;End Session&quot; dialog in KDE"
date: 2007-03-01
forum: Desktop Environments
---

### Post by elempoimen on 2007-03-01
In Ubuntu, when I press the power button on my hp laptop, it brings up the shutdown options dialog (log off, cancel, hibernate, suspend, restart). I've now switched to KDE, but when I hit the button, it simply initiates the shutdown sequence for Linux, rather than giving me the "End Session" dialog. I would prefer that I get that "End Session" dialog--is there a way to make that happen in KDE?

---

### Post by g8m on 2007-03-01
I suppose you have to change /etc/acpi/powerbtn.sh

This is will do standard.

# Otherwise, if KDE is found, try to ask it to logout.
# If KDE is not found, just shutdown now.
if ps -Af | grep -q '[k]desktop' && pidof dcopserver > /dev/null && test -x /usr/bin/dcop ; then
    /usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 0 2 0 && exit 0
fi

I am on gnome, so I dont know what progam is called with the normal logout.

---

