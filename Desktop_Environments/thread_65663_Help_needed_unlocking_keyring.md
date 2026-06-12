---
title: "Help needed unlocking keyring"
date: 2005-09-14
forum: Desktop Environments
---

### Post by Blackie_Chan on 2005-09-14
Everytime that I try to use 'File Browser' (Nautilus) to view samba shares, I get an annoying window titled 'Unlock Keyring', which prompts me for the password of the default keyring (which I don't know). In the window it says "The 'application File Manager'(/usb/bin/nautilus) wants access to the default keyring, but it is locked.

Anyhow, how do I get rid of this annoying window? Can't I just view the shares, without being prompted for a password.

---

### Post by twowheeler on 2005-09-14
Well, if you delete the keyring directory it will delete all stored passwords and let you set a new password.

```
rm -rf ~/.gnome2/keyring/
```

---

