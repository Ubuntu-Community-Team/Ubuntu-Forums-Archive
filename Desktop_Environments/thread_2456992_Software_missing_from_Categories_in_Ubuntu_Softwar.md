---
title: "Software missing from Categories in Ubuntu Software Store v.20.04.1 LTS"
date: 2021-01-23
forum: Desktop Environments
---

### Post by jgwokas on 2021-01-23
Hello Ubuntu Community!

Strange issue with Ubuntu Software Store(?) v.20.04.1 LTS

When I click on any Categories icon in the Ubuntu Software Store(?), there is no software to be found, nowhere.

Any ideas why this may be?

Cheers!

---

### Post by CelticWarrior on 2021-01-23
Welcome.

Please click the big button with the 3 dots, wait some seconds.

---

### Post by jgwokas on 2021-01-23
> **CelticWarrior said:**
> Welcome.

Please click the big button with the 3 dots, wait some seconds.

Thanks CelticWarrior. Works for some, but not all. Any ideas why it's setup that way?

---

### Post by CelticWarrior on 2021-01-23
It's how it works now, far from perfect.

---

### Post by jgwokas on 2021-01-23
> **CelticWarrior said:**
> It's how it works now, far from perfect.

Interesting. I don't remember it working that way in the past. Why the change?

---

### Post by Dennis N on 2021-01-23
If you have problems with Ubuntu Software (a snap package), install Gnome Software (a normal package). Gnome Software (icon is 'Software') has the added ability of searching for Flatpak packages*, plus it will automatically update Flatpak. These Software managers can coexist (see the screenshot). 

*requires gnome-software-plugin-flatpak

Comment: My Ubuntu Software does work correctly, so the behavior you see of software missing from some catgories isn't normal. It can take 10 seconds or so to load up a category, and they load here without pressing the dots. Gnome Software is more responsive, in my opinion.

---

### Post by jgwokas on 2021-01-23
I appreciate your response, Dennis. Thank you.

How would I go about installing the Gnome Software package?

---

### Post by ActionParsnip on 2021-01-23
Could use apt. Nice and easy

---

### Post by grahammechanical on 2021-01-23
I have the same thing happening with the app called Software and Details shows that this is not a snap version but from Gnome. In my case, once I click on the 3 dots  the icons appear and if I try other categories then the icons appear after a few seconds without clicking the 3 dots.

Regards

---

### Post by Dennis N on 2021-01-24
> **jgwokas said:**
> I appreciate your response, Dennis. Thank you.

How would I go about installing the Gnome Software package?

The simplest way is to use the terminal:
```
sudo apt install gnome-software
```
If you need or want Flatpak package support, you also need to get gnome-software-plugin-flatpak. It may or may not be automatically installed.
If this solves your problem, you could remove ubuntu-software if you want. It's package name is snap-store.
```
snap remove --purge snap-store
```

---

