---
title: "Desktop damaged, how to restore?"
date: 2010-03-03
forum: Desktop Environments
---

### Post by klaasvg on 2010-03-03
Hello,
I am a confident Karmic user, but experienced a little with different desktop themes. Now I have a few problems. First, the context menu from the upper menu bar is damaged, it showls only the items "Help" and "About panels". But no option to add or remove applets, which worked normally before.
Second, the context menu from the pulldown menu is also damaged, before I was able to use the context menu to add a ahortcut to the desktop. Now, using the right button, the application is launched, just as if I use the left button.
Anyway knows what has happened? And how to fix/reinstall this functionality?
TIA, Klaas

---

### Post by Barriehie on 2010-03-07
Try reinstalling gnome-panel.

---

### Post by c0nfusedami on 2010-03-07
How would one go about reinstalling that program?

---

### Post by Barriehie on 2010-03-07
> **c0nfusedami said:**
> How would one go about reinstalling that program?

Either the GUI, synaptic, or from the terminal:
```

sudo aptitude reinstall gnome-panel
```
...it will reinstall the package...
```

exit

```

Unless versed in the use of the terminal you might should use the GUI, System > Administration > Synaptic Package Manager.  Search, gnome-panel, right mouse, reinstall, apply, done. Logout, and then back in.

HTH

---

### Post by c0nfusedami on 2010-03-08
Thank you

---

### Post by Barriehie on 2010-03-08
> **c0nfusedami said:**
> Thank you
Your welcome, so that worked out for you?

---

### Post by klaasvg on 2010-03-09
For me it didn't (tried it before), but I fixed in another way. I discovered I messed up Gnome anel settings by installing a Windows-like theme and used its uninstall function to remove it again. By resetting the Panel settings the normal functionality returned:
gconftool-2 --recursive-unset /apps/panel (reset the settings to default)
pkill gnome-panel (kill and rstart panels)

---

### Post by Barriehie on 2010-03-09
Is this solved?

---

### Post by dadgetboy on 2010-03-09
To completely reset Gnome

Press Ctrl+Alt+F1

Type in:

```
**sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity**
sudo reboot
```


That is all, Gnome has been reset to original, out of the box settings.

---

### Post by klaasvg on 2010-03-09
> **Barriehie said:**
> Is this solved?

Yes for me it is!

---

### Post by Barriehie on 2010-03-09
> **klaasvg said:**
> Yes for me it is!

Perhaps mark the thread as solved for the searching crowd! 8)

---

