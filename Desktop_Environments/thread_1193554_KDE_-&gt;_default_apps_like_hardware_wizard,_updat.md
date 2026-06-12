---
title: "KDE -&gt; default apps like hardware wizard, update manager, package manager?"
date: 2009-06-21
forum: Desktop Environments
---

### Post by DeusExM1 on 2009-06-21
I have recently uninstalled gnome and everything that came with it, and just installed kubuntu-desktop with everything it recommended on my system. However now i am lacking:

1. Software package manager: So how am i supposed to install new software? What is the default KDE package manager and how do i install it in the terminal? Im looking for the equivalents of gnome "add/remove" and "synaptic package manager" 

2. Update manager: I can see that updates are available on the bottom right (an icon appears) but i cannot install anything because when i click on it nothing happens. So what is the default update manager in KDE and how do i install it via terminal?

3. what is the KDE found new hardware wizard? The one in gnome correctly installs my video card drivers, so i need something like that. 


Any ideas guys ?

---

### Post by aged hippy on 2009-06-22
The default KDE 3.5 package manager is Adept, with KDE 4.x it is KPackageKit, although Synaptic works with both desktops. :)

If you open a terminal and copy/paste in it:
```

sudo apt-get install synaptic

```
it will install *guess what* for you. :)

I wouldn't recommend the KPackageKit, it seems to be broken at the moment, and it won't work if you're using the KDE 4.x desktop.
***Edit:*** and it won't work anyway if you're using the **_KDE 3.5_** (not KDE 4.x) desktop.

---

