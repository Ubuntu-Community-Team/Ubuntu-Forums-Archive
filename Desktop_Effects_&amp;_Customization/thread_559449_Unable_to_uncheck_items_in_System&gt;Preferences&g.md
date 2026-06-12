---
title: "Unable to uncheck items in System&gt;Preferences&gt;Main Menu!"
date: 2007-09-25
forum: Desktop Effects &amp; Customization
---

### Post by apricot on 2007-09-25
Sudo alacarte working fine but other users unable to remove or add items in Main menu. Can somebody fix it?

---

### Post by Forlong on 2007-09-25
> **apricot said:**
> Sudo alacarte working fine
That's exactly the problem. You don't need to run alacarte being root. Now that you did it, the config is only to change with sudo.

Try this in the terminal to gain complete access to your home directory again:
```
sudo chown $USER:$USER $HOME -R
```
Then this:
```
chmod -R u+rwX $HOME
```

---

### Post by apricot on 2007-09-25
That worked! Tnx!

---

