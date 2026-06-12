---
title: "how to revert to default KDE desktop"
date: 2006-01-19
forum: Desktop Environments
---

### Post by Apostata on 2006-01-19
Hello,

  In the event that I upgrade (or try a Dapper beta), I'd like to find out how I can bypass my existing KDE desktop settings - is there a file/folder (assumedly in ~/.kde) that needs to be renamed in order to have this happen?

Thanks in advance...

---

### Post by zAo on 2006-01-19
For KDE ~/.kde will do. For Gnome ~/.conf and ~/.gnome2 will do.

---

### Post by Apostata on 2006-02-01
Sorry for the late response, but deleting ~/.kde will wipe out more than just my desktop settings would it not? There's a /kmail folder with my account settings in there, as well as several other folders which would directly affect other KDE apps.  Am I wrong?

---

### Post by Apostata on 2006-02-03
*bump* anyone else know of a clean way to dump desktop settings?

---

### Post by apswartz on 2006-02-03
rename your .kde folder to something like .kde_OLD

Then copy the settings you want to save into your new .kde folder (e.g., kmailrc etc.)

---

### Post by Neo Ex on 2006-02-03
I'm not sure I've understood: you'd like to come back to KDE default settings? You don't want Kubuntu default settings?
It you mean this, I have a solution: uninstall kubuntu-default-settings (you must also uninstall kubuntu-desktop) and remove the .kde folder. I've also installed kpersonalizer (the wizard which compares when you log in KDE for the first time).

---

