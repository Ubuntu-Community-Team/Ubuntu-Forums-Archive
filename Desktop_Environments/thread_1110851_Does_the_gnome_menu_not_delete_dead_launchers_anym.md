---
title: "Does the gnome menu not delete dead launchers anymore??"
date: 2009-03-30
forum: Desktop Environments
---

### Post by pluckypigeon on 2009-03-30
I was wondering if this is a new feature?

When I uninstall something I have to remove the program.menu file or delete the entry with alacarte. Is this right?

rm -rf .gnome .gnome2 .gconf .gconfd .metacity doesn't change anything.

Just curious:)

Thanks

---

### Post by mcduck on 2009-03-30
Has it ever done that? As far as I know it hasn't.

Launchers created automatically when installing things with package manager are removed if you uninstall the package, but all launchers you add yourself (or any launchers you move or edit) will stay until you remove them yourself.

---

### Post by pluckypigeon on 2009-03-31
> **mcduck said:**
> Has it ever done that? As far as I know it hasn't.

Launchers created automatically when installing things with package manager are removed if you uninstall the package, but all launchers you add yourself (or any launchers you move or edit) will stay until you remove them yourself.

I reverted the menu and it didn't make any difference.

I must have edited something in /usr/share/applications or elsewhere.

It's not a big deal for me anyway.

If I ever find out, I'll post the reason why it's happened.

Thanks

---

