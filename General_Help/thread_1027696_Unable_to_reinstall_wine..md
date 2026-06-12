---
title: "Unable to reinstall wine."
date: 2009-01-01
forum: General Help
---

### Post by phaedrus85 on 2009-01-01
I am running ubuntu 8.10, with all updates accepted. I've attempted to re-install WINE by uninstalling it and reinstalling it via my Add/Remove. Somehow, I think I've managed to not completely uninstall it, and now cannot re-install it. When typing
sudo apt-get install wine     I get this error message:
The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed



I originally uninstalled wine by typing in terminal:

sudo apt-get autoremove wine

When viewing hidden files in Home Folder, there is no .wine folder.

I'm not sure what to do at this point to reinstall wine. I cannot install it via Synaptic Package Manager nor Add/Remove. Any suggestions?

---

### Post by mc4man on 2009-01-01
Check your sources here and or look in System -> Admin....-> software sources.  Also ck. in synaptic for libsound2. Either your trying to install  libsound2 1.0.15-3ubuntu4 or it's the version installed

You should have ver. 1.0.17a-0ubuntu4, either installed or available to be installed

```
cat /etc/apt/sources.list
```


In other words libsound2 1.0.15-3ubuntu4 is the hardy version

---

