---
title: "How 2 Disabe menu editor?"
date: 2011-03-28
forum: Desktop Environments
---

### Post by mrandredparis on 2011-03-28
Hi,
  Could you please tell me how to disable the gmenu-simple-editor?  When you right click on the panel you are given the option of editing the menu.  I would like to disable the option or remove it altogether.  I have U10.10.  I tried to chown it something less 700 or 744 but that didn't work, the user has desktop rights, not administrator.  Any ideas would be greatly appreciated.  Thanx in advance.

---

### Post by Krytarik on 2011-03-28
Purge the package "alacarte", it will remove "ubuntu-desktop" as well, because it is listed as dependency to it, but it is just a metapackage, meaning no real apps will get removed:
[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

Greetings.

---

### Post by mrandredparis on 2011-03-28
> **Krytarik said:**
> Purge the package "alacarte", it will remove "ubuntu-desktop" as well, because it is listed as dependency to it, but it is just a metapackage, meaning no real apps will get removed:
[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

Greetings.

tried this already, but it leaves the gmenu-simple-editor as it's replacement

---

### Post by Krytarik on 2011-03-28
Did you already try to rename the executable or place it somewhere else, not just change its permissions?

---

### Post by mrandredparis on 2011-03-28
> **Krytarik said:**
> Did you already try to rename the executable or place it somewhere else, not just change its permissions?

tried renaming it but it wouldn't allow me to

---

### Post by Krytarik on 2011-03-28
> **mrandredparis said:**
> tried renaming it but it wouldn't allow me to
Eh, why!? You used 'sudo', right? Maybe you need to logout and do it from the console.

---

### Post by mrandredparis on 2011-03-28
> **Krytarik said:**
> Eh, why!? You used 'sudo' right? Maybe you need to logout and do it from the console.

yes that worked thank you, for some strange reason i made the n00b error of not typing sudo

---

