---
title: "[SOLVED] Valid Values in .Desktop Files"
date: 2007-09-23
forum: Desktop Environments
---

### Post by undecidable on 2007-09-23
When creating a new .desktop file (eg to create a new template)
I just copy an existing one, eg TextFile.desktop,
and modify it.

One line in the .desktop files has me mystified:
  X-Ubuntu-Gettext-Domain 
which has values such as:  desktop_kdebase or desktop_koffice

I seem to be able to use  desktop_kdebase as the value for all sorts of templates
(eg OOO Spreadsheets), but am worried about proceeding blissfully in ignorance.

Does anyone know of a reference for X-Ubuntu-Gettext-Domain values
and what they mean  (eg desktop_kdebase, desktop_koffice,..)

Or, more generally, where can I find a reference for what goes in a .desktop file?

---

### Post by Wolki on 2007-09-23
> **undecidable said:**
> 
Does anyone know of a reference for X-Ubuntu-Gettext-Domain values
and what they mean  (eg desktop_kdebase, desktop_koffice,..)

A Key starting with an X indicates that it's not an official component of a .desktop file, but an extension done by a vendor for their personal use.

I've wondered to what it exactly means, here's what I think:
X: Vendor-specific addon
Ubuntu: The vendor that made this addon
Gettext-Domain: Domain(?) of he software that handles translations in applications
 
So it probably has something to do with translations. gettext should work without it, so it probably has to do with the Ubuntu translation infrastructure.

You can probably just delete this key in your own desktop files.

> Or, more generally, where can I find a reference for what goes in a .desktop file?

Official spec is at: [http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec](http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec)

---

### Post by undecidable on 2007-09-23
Wolki, thanks very much.
(googling ".desktop" is unhelpful - google insists on ignoring the ".")

[http://www.freedesktop.org/wiki/Spec...top-entry-spec](http://www.freedesktop.org/wiki/Spec...top-entry-spec) was v. helpful.
Wasn't sure what gettext was,
so checked it at [http://www.gnu.org/software/gettext/](http://www.gnu.org/software/gettext/).
I think I understand the issue now.

Most .desktop files seem to use desktop_kdebase
for X-Ubuntu-Gettext-Domain
so that seems the safest default.

---

