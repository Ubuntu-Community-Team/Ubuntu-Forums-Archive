---
title: "Wine won't install anything (Jaunty)"
date: 2009-05-19
forum: General Help
---

### Post by inverseroom on 2009-05-19
When I try to get wine to open an executable, I get this message:

> Warning: could not find DOS drive for current working directory '/home/lennon/Desktop', starting in the Windows directory.
wine: could not load L"C:\\windows\\system32\\iview423_setup.exe": Module not found


The module is indeed there.  I get the same message if I try to open it from /tmp or from the home folder, too.

So I tried just copying the IrfanView folder from my Windows machine over to .wine/drive_c/Program Files, and then opening iview_32.exe with wine, and nothing happens at all.

I installed Wine, uninstalled it, reinstalled it, no go.  This is on a brand new HP laptop running a fresh install of Jaunty, alongside a Vista partition.  Everything else is working great in both OSes, with only a day or so of tweaks to get Jaunty just the way I wanted it.

Help!!

---

### Post by inverseroom on 2009-05-19
Oh and also, I went to the WineHQ tutorial page, added their repository, and updated.  Now, when I try to open the exe's, I get the little spinning working symbol for five seconds or so, and THEN nothing happens.

Is Wine somehow confusing /drive_c/ with the C: in my Windows partition?

---

### Post by michy99 on 2009-05-19
Do you have a copy of MFC42.dll in ~/.wine/drive_c/windows/system32?

---

### Post by inverseroom on 2009-05-19
> **michy99 said:**
> Do you have a copy of MFC42.dll in ~/.wine/drive_c/windows/system32?

Yes, most definitely.  I was kind of surprised, actually, to see that it was already there after my Wine installation.  This was not the case back when I was on Hardy.

---

