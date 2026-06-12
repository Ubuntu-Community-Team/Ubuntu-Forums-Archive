---
title: "Can't install program in WINE"
date: 2006-01-26
forum: Desktop Environments
---

### Post by Knight Palatine on 2006-01-26
I'm trying to install the stamps.com program in WINE. When I launch the installer, it goes through the normal routine of license acceptance and default installation directory, then tells me I need Administrator privileges to install.

It looks like I have all necessary permissions for WINE and for the stamps.com installer. Anyone have a clue what's going on?

---

### Post by pelle.k on 2006-01-26
Just a quick check, are you using the latest 0.9.6 version of wine?
Are you running this program in win2000 compability mode?

---

### Post by Knight Palatine on 2006-01-26
[QUOTE=pelle.k]Just a quick check, are you using the latest 0.9.6 version of wine?
Are you running this program in win2000 compability mode?[/QUOTE]

Yes to both.

You gave me an idea. I switched WINE to Win98 mode. Now it says I need to install IE 4.0. I'll give it a go when time permits.

Thanks,
Daryl

---

### Post by pelle.k on 2006-01-27
That should be easy enough.
If you happen to own a win98 cd (like i do, shame on me ;) ) remember that extracting all .dll:s from the cabs, and copying them to /home/YOURNAME/.wine/drive_c/windows/system often works best, simply because "real" dlls is - the real deal, instead of those built in.

---

