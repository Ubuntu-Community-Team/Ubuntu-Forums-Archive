---
title: "Can't run add and remove"
date: 2006-08-11
forum: Desktop Environments
---

### Post by geovino on 2006-08-11
When I try to use add and remove I get this:

need to run dpkg --config -a
but when I do it won't complete. this is what it says:

davek@davek-desktop:~$ sudo dpkg --configure -a Password:
Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...

and it just hangs there. How can I fix this?

---

### Post by orasis on 2006-08-11
> **geovino said:**
> When I try to use add and remove I get this:

need to run dpkg --config -a
but when I do it won't complete. this is what it says:

davek@davek-desktop:~$ sudo dpkg --configure -a Password:
Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...

and it just hangs there. How can I fix this?

I would try re-installing flash, if that does not work remove it from your share directories manually.

---

### Post by geovino on 2006-08-11
The flashplugin has been nothing but trouble. I got back into Synaptic and did a complete removal of it and then I got this error:

E: Not locked

What's that?

---

### Post by Ubunted on 2006-08-11
```
apt-get -f install flashplayer-plugin
```

Worked for me.

---

