---
title: "Lost Windows on Minimization"
date: 2014-02-24
forum: Desktop Environments
---

### Post by rbscairns on 2014-02-24
I am using Ubuntu 12.04 with Gnome Classic.

Recently i found that I loose a running program when I minimize its window. It no longer appears in the pannel at the bottom of the screen. Is there a way to get this feature back?

---

### Post by coldraven on 2014-02-24
AFAIK there is no longer a bottom panel. You should be able to find the application in any of the workspaces by pressing Winkey + S. (Winkey is called the "Super" key in Ubuntu)
You can drag applications to a different workspace.

---

### Post by ibjsb4 on 2014-02-24
I have had this happen on new installs, before I have updated.  Are you updated?

In terminal:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by rbscairns on 2014-02-24
Coldraven, as stated in my OP, I am using Ubuntu 12.04 **with Gnome Classic**.  This incorporates a pannel (bar) at the bottom of the screen that includes window selection and (normally) icons to restore minimized windows. It is the icons that are not displaying when I minimize a window.

Ibjsb4, my system is up-to-date, reporting ```
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

---

### Post by ibjsb4 on 2014-02-24
Tried the usual fixes?

```
sudo dpkg --configure -a
sudo apt-get -f install
```

Could also try reinstalling the panel, your panel configurations are in ~/.config

Edit: Are you running compiz or metacity?

---

### Post by rbscairns on 2014-02-25
> **ibjsb4 said:**
> Tried the usual fixes?

```
sudo dpkg --configure -a
sudo apt-get -f install
```

Could also try reinstalling the panel, your panel configurations are in ~/.config

Edit: Are you running compiz or metacity?

I ran the code and removed all unused packages. The problem persists.

I am not running compiz or metacity.

My thinking is to uninstall Gnome Classic and reinstall it. How do I uninstall Gnome Classic?

---

### Post by Frogs Hair on 2014-02-25
Have you checked to see if the window list is activated in the add to panel menu . It is possible to remove it from the panel . You can try Alt + Right Click or Super Key + Alt Right Click select add to panel and select window list to be added .

---

### Post by rbscairns on 2014-03-02
Alt + right click on the bottom panel (and top panel) works and allows me to add items to the panel, but that is not my problem.

My problem is when I minimize a window. It does not show an item in the bottom panel.

Any ideas on how to remove Gnome Classic so that I can try to reinstall it?

---

### Post by ibjsb4 on 2014-03-02
> **rbscairns said:**
> Any ideas on how to remove Gnome Classic so that I can try to reinstall it?

```
sudo apt-get remove --reinstall gnome-session-fallback
```

---

### Post by rbscairns on 2014-04-20
Sorry for the late reply. I have been at sea.

Frogs Hair solved my problem. Here is what I did:

[LIST=1]
[*]Super Key + Alt Right Click in the bottom panel
[*]Click on "Add to Panel"
[*]Scroll down and select "window List"
[*]Click on "Add"
[/LIST]
Now all is back to normal.

Thank you Frogs Hair.

---

