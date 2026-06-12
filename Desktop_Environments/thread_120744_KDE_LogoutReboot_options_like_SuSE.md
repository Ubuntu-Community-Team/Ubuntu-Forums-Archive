---
title: "KDE Logout/Reboot options like SuSE"
date: 2006-01-23
forum: Desktop Environments
---

### Post by bennettg on 2006-01-23
Hi.  nOOb here.

Just switched from opensuse 10.  In suse's kde desktop, when one goes to kmenu--->logout--->restart there is a pull down menu that allows you to choose what os you want to reboot in without having to do it in grub.  so when i logged out, i could automatically reboot into windows if i needed.

can anyone tell me how to do this in kubuntu?  i searched the forums here and at linuxquestions.org without success.

---

### Post by Sp@z on 2006-01-23
that wouls certainly be a nice touch to kubuntu.

---

### Post by teprrr on 2006-01-24
AFAIK this is possible only with LILO, but I can't be sure about it.

---

### Post by Adrian on 2006-01-24
[QUOTE=teprrr]AFAIK this is possible only with LILO, but I can't be sure about it.[/QUOTE]

SUSE's KDE does it with GRUB, so there must be some solution :)

---

### Post by obibok on 2006-01-24
Have you tried setting GRUB in KDM shutdown options?

**# kdesu kcmshell kdm**

*Shutdown->Miscellaneous->Boot Manager: GRUB*

---

### Post by bennettg on 2006-01-24
[QUOTE=obibok]Have you tried setting GRUB in KDM shutdown options?

**# kdesu kcmshell kdm**

*Shutdown->Miscellaneous->Boot Manager: GRUB*[/QUOTE]

perfect!!!!  thanks

---

### Post by GameManK on 2006-03-23
That's a nice feature! Should be enabled by default.

Thanks to whoever here filed the bug:
[https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/29684](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/29684)

---

### Post by Zoso183 on 2008-07-05
Sorry to reply to a very old thread but I'm trying to get this to work in 8.04 and setting the boot manager to grub under the login manager has not changed the log out.  When I click the log out button I get the same five buttons to select from, but no menu to allow a direct reboot into windows.  Anyone able to help?

Thanks,
Andy

---

