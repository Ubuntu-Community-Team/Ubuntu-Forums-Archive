---
title: "Clearlooks-cairo, gtk-engines"
date: 2006-07-21
forum: Desktop Environments
---

### Post by lucis on 2006-07-21
I'm trying to install this theme [http://art.gnome.org/themes/gtk2/1213](http://art.gnome.org/themes/gtk2/1213). The description says that it requires clearlooks-cairo which I presume I am missing considering the theme won't work when I try to apply it. 

In order to install clearlooks-cairo I downloaded the latest source tarball of gtk-engines from Gnome's FTP. I compiled it and used checkinstall to generate a deb package which I then installed.

However, the theme is still not working. Is it because the new version of gtk-engines isn't taking precedence over the older one? How could I solve this?

Thanks.

---

### Post by Jagot on 2006-07-21
[http://ubuntuforums.org/showthread.php?t=89056](http://ubuntuforums.org/showthread.php?t=89056)

---

### Post by lucis on 2006-07-21
> **Jagot said:**
> [http://ubuntuforums.org/showthread.php?t=89056](http://ubuntuforums.org/showthread.php?t=89056)

Uh? That thread is 19 pages of information that doesn't apply to me. The packages provided are for Breezy.

---

### Post by Jagot on 2006-07-21
It provides the patch for the cairo enabled clearlooks, which people on there are saying works in Dapper:

[http://ubuntuforums.org/showpost.php?p=751338&postcount=178](http://ubuntuforums.org/showpost.php?p=751338&postcount=178)

---

### Post by lucis on 2006-07-21
> **Jagot said:**
> It provides the patch for the cairo enabled clearlooks, which people on there are saying works in Dapper:

[http://ubuntuforums.org/showpost.php?p=751338&postcount=178](http://ubuntuforums.org/showpost.php?p=751338&postcount=178)

I installed the provided package and it's still not working. Doesn't the new version of gtk-engines support cairo? I just need to get it to take precedence over the old one, AFAIK.

---

### Post by lucis on 2006-07-21
Nevermind, I got it! Turns out the new gtk-engines did have what was needed, it was just being installed in the wrong place.:)

---

