---
title: "Some menu items wont load!!"
date: 2006-07-27
forum: Desktop Environments
---

### Post by declaration on 2006-07-27
Hi,

Having a slight problem here. When logged in as normal user, I try and load menu items via the menu such as "disks-admin" or "network-admin" or "update-manager" etc and a password box comes up. I put my password in, the loading icon comes on for a second but then nothing happens. Nothing.

If i open them via terminal, eg

sudo update-manager, they open. 

Apps seem to open fine via the menu.

Help would be much appreciated.

---

### Post by declaration on 2006-07-27
even synaptic wont load from the menu. Only through terminal.

---

### Post by declaration on 2006-07-28
sorry to bump- but anyone have any ideas?

---

### Post by christhemonkey on 2006-07-28
Well for starters when opening graphical applications from a terminal,
you should use *gksudo* instead of sudo.
So:
```
gksudo synaptic 
```

And then the errors might help with the whole, menu doesnt open stuff problem.

---

### Post by declaration on 2006-07-28
Thanks. But even when using the gksudo command, synaptic loads straight away with no errors.

---

