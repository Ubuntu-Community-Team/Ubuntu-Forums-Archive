---
title: "Why doesn't Xchat get updated with my Ubuntu?"
date: 2006-01-07
forum: Desktop Environments
---

### Post by mog27 on 2006-01-07
XCHAT is up to 2.6.1 however I just have 2.4.4.  Perhaps I am missing something in my sourcles.list? I apt-get upgrade regularly.

---

### Post by nix4me on 2006-01-07
Add the backports repository to your /etc/apt/sources.list

xchat is upgraded to 2.6.0 in backports.

nix4me

---

### Post by CookieNinja on 2006-01-07
probably just because the very newest version hasn't been officially packaged into a .deb and added to repositories. I wouldn't bother, either, personally, unless there's a specific feature you want that's specific to that version, or some bug that annoys you that's been fixed in the new version.

---

### Post by nix4me on 2006-01-07
Add the backports, and 2.6.0 is all yours.  Simple as that.

nix4me

---

### Post by MasJ on 2006-01-11
The 'feature' in Xchat 2.6.1 is the DCC AutoGet can be enabled. In 2.6.0 this feature is absent.

---

