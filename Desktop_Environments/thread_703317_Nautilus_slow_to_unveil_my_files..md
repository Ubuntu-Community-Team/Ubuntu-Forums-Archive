---
title: "Nautilus slow to unveil my files."
date: 2008-02-21
forum: Desktop Environments
---

### Post by QwUo173Hy on 2008-02-21
When I open folders such as ~/Music (655 folders) or ~/Video (400 files and on separate drive) - it takes from 0 - 20 seconds to display the contents.

I've tried disabling previews but it doesn't make a difference, and isn't relevant for the Music folder as it only contains folders.

Does anyone know what causes this? I'm thinking I should file a bug report and I'm browsing launchpad.net as well as bugzilla.org as I write this.

Regards,
Jarlath

---

### Post by MCrittenden on 2008-02-21
I won't be any help except to say that I had the same prolbem after installing Gutsy just after it was released. I searched and searched for an answer, and finally gave up and installed Thunar instead. I had to reinstall Gutsy this weekend for a different reason, and now Nautilus works perfectly. Perhaps a Nautilus bug that was fixed between October and now? When did you download Gutsy? Is reinstalling an option, or would that be too much trouble to be worth it?

Ironically, now that Nautilus works fine, I like Thunar too much to switch back.  Pint being: if all else fails, you could always try a different file manager.

---

### Post by QwUo173Hy on 2008-02-22
Hi MCrittenden,
I've just discovered last night that running 'killall nautilus'. Solves it. When nautilus comes back up, it's as responsive as I could ever hope for. I'll add this to the bug report at bugzilla - but I've heard from a developer that the new Gnome being released in about 3 weeks has a completely new backend for Nautilus so those bugs might become irrelevant.

I might try Thunar.

All the best,
Jarlath

---

### Post by elleipein on 2008-02-22
I had a problem much like that. I resolved the problem by changing the preferences for previewing files to never. 

more information here [Nautilus Preferences]("https://help.ubuntu.com/7.04/user-guide/C/nautilus-preferences.html")

---

