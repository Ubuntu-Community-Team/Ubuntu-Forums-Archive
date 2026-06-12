---
title: "backup and restore vino-preferences settings"
date: 2013-05-19
forum: Desktop Environments
---

### Post by cccc on 2013-05-19
HI

Howto backup and restore on other machines [vino-preferences]("https://wiki.archlinux.org/index.php/Vino") settings under LXDE?

---

### Post by steeldriver on 2013-05-19
Does LXDE use dconf under the hood now? in the regular Ubuntu desktop, you can install the dconf-tools package and then do

```

dconf dump /desktop/gnome/remote-access/ > vino-prefs

dconf load /desktop/gnome/remote-access/ < vino-prefs

```

---

### Post by cccc on 2013-05-19
> **steeldriver said:**
> Does LXDE use dconf under the hood now? in the regular Ubuntu desktop, you can install the dconf-tools package and then do

```

dconf dump /desktop/gnome/remote-access/ > vino-prefs

dconf load /desktop/gnome/remote-access/ < vino-prefs

```

Thx a lot, but this is a self-made thin client, dconf-tools are not installed and is not allowed to install any applications on it.
I would like to copy just a file.
Which file is it exactly, perhaps from the /home/user directory?

---

