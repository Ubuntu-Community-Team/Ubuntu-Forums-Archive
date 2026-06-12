---
title: "Desktop Darkens When Prompted for Password"
date: 2011-05-25
forum: Desktop Environments
---

### Post by asalina on 2011-05-25
In some cases when prompted for a password the entire desktop is darkened while the pop-up window waits for input. Launching Synaptic Package Manager is a good example.

How can I turn off this darkening effect? I often work at the computer with the room lights off and with the desktop darkened like that I find it hard to see my keyboard (I'm not joking!) in order to supply the password.

Thanks

EDIT: I'm using 11.04 w/ Classic -- No Effects.

---

### Post by wojox on 2011-05-26
Open a terminal and run this:

```
gconftool-2 --type boolean --set /apps/gksu/disable-grab "True"
```

---

### Post by asalina on 2011-05-26
Thank you, wojox. That did the trick.

---

