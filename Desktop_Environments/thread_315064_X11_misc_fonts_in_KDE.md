---
title: "X11 misc fonts in KDE"
date: 2006-12-08
forum: Desktop Environments
---

### Post by dirtside on 2006-12-08
I'm using Dapper Drake.  In /usr/share/X11/fonts/misc, there are a number of bitmapped fonts, such as (my favorite) 7x13.pcf.  I want to use this font in my terminal (gnome-terminal), but I can't figure out how.  Fontconfig seems to detect that there's fonts there, but KDE won't show them.  If I try to install the font (using Settings > System Administration > Font Installer), it pretends to install the font but won't show it in the list.  (This is different from when I try to install something that's not a font, it actually gives an error in those cases.)

Any ideas?  I've been poking around trying to figure out how fontconfig actually decides what fonts are available (like, where does fc-list actually pull that list from?) but I'm out of ideas. ](*,)  Thanks in advance.

- dirtside

---

### Post by ajgreeny on 2006-12-08
You need to install fonts as root to do this, I think.  In kde open *system settings* or *kcontrol* (KDE Control Centre) and click on the Administrator Mode button first, then install the fonts.  I think they will then be available for almost anything.  Just be aware that some fonts are not available for use in the terminal; I'm not certain why but that seems to be so, and may just be the reason for your problem.

---

### Post by dirtside on 2006-12-11
I've used Administrator Mode every single time (even tried doing it without that).  Never works.  If I try to install those same fonts again, sometimes it'll ask me if I want to overwrite the old one (which has a size listed as "0 bytes").

Anyone have any idea what configuration files the Font Installer writes to?  I'd like to look and see why it thinks it's installed those fonts without actually having done so.  Thanks.

---

