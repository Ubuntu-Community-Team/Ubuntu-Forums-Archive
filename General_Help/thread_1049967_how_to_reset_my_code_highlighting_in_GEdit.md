---
title: "how to reset my code highlighting in GEdit"
date: 2009-01-25
forum: General Help
---

### Post by NinjaWork on 2009-01-25
I killed my code highlighting in GEdit for Perl when I copied a file to use for cgi highlighting.

Anyone know how to reset GEdit? I tried to reinstall, but it didn't work.

TIA!

---

### Post by mb_webguy on 2009-01-25
The settings for gedit (and other applications) are located in your home directory.  Delete the ~/.gconf/apps/gnome-settings/gedit directory to wipe out your current configuration.  You may have to reinstall gedit after this, but I doubt it.

---

### Post by NinjaWork on 2009-01-25
hi mb_webguy, thanks for the reply. I also had copied:

/usr/share/gtksourceview-1.0/language-specs/perl.lang
/usr/share/gtksourceview-2.0/language-specs/perl.lang

as

/usr/share/gtksourceview-1.0/language-specs/cgi.lang
/usr/share/gtksourceview-2.0/language-specs/cgi.lang

so I guess I'm going to give your solution a shot and maybe remove the cgi.lang files I added.

thanks again!

---

