---
title: "Last Kubuntu update; local language and Xorg faillure"
date: 2005-03-27
forum: Desktop Environments
---

### Post by WimVriend on 2005-03-27
Hi,
After the last upgrade I am missing my local language (dutch) and I can't reinstall it. Everything is now back in english. And there is a problem with Xorg. When I log out and then back in, I have two warning messages.

The composite manager crashed twice within a minute and is therefore disabled for this session.

The second warning is
Composite extensions not found
You must use Xorg >6.8 for translucency and shadows to work.
Additionally, you need to add a new section to your config file.

Section "Extensions"
Option "Composite" "Enable"
Endsection

And there is nothing chanced, i made only the necessery update/upgrade

Wim

---

### Post by mkisiu on 2005-03-28
Hi,
I have exactly the same problem. After last update my locale settigs went away :-(
I've tried to reinstall necessary i18 file but it's doesn't correct the situation.
Does anybody know what's going on?

Best regards
Maciek

---

### Post by bantu on 2005-03-30
Update again. Things should be working again (same happened here, but fixed now)...

---

### Post by fdoving on 2005-03-30
[QUOTE=bantu]Update again. Things should be working again (same happened here, but fixed now)...[/QUOTE]
 I had the locale problem yesterday.. it should be fixed now..

---

### Post by fdoving on 2005-03-30
I had the same locale problem yesterday, it should be fixed now, in the ubuntu3 packages.

---

