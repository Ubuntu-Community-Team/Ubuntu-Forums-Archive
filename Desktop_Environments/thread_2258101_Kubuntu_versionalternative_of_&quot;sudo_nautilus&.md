---
title: "Kubuntu version/alternative of &quot;sudo nautilus&quot;?"
date: 2014-12-24
forum: Desktop Environments
---

### Post by Tornikee on 2014-12-24
On Ubuntu I used to enter the "sudo nautilus" command to get permissions to paste folders (such as those for icon themes) into the home folder (usr/share/icons specifically). I just installed Kubuntu 14.10 Plasma 5 and can't find what its alternative to that command is. Can anybody provide any tips how to change/bypass/etc home folder permissions?

---

### Post by schragge on 2014-12-24
kdesudo dolphin

---

### Post by Tornikee on 2014-12-24
Thanks for that. Is it the same in Linux Mint and Xubuntu? I just tried it in Mint and the command didn't open the file manager.

---

### Post by deadflowr on 2014-12-24
> **Tornikee said:**
> Thanks for that. Is it the same in Linux Mint and Xubuntu? I just tried it in Mint and the command didn't open the file manager.

No Kubuntu(kde) and Xubuntu(xfce) are different.
KDE is particularly different from the other desktop environments.
Usually the others are fine with the graphical sudo called gksu, or gksudo.

As for Mint, well that's is not a desktop but a Linux distribution, so it's use of a graphical sudo would be dependent upon what desktop is used.
I know mint has several desktops to choose from.

---

### Post by Tornikee on 2014-12-25
Thank you.

---

### Post by flaymond on 2014-12-25
It depend on what File Manager your distro use. Like Lubuntu, the default File Manager is pcmanfm, Xubuntu is Thunar and Ubuntu is nautilus...for Linux Mint..I believe it Nemo

Just like deadflowr said - Usually run it will be fine if you run it with gksudo/gksu

This is the list include the safe command -

1. Nautilus (for Ubuntu)
```
 gksudo nautilus 
```

2. Thunar (for Xubuntu)

```
 gksudo thunar 
```

3. PcManFm (for Lubuntu)

```
 gksudo pcmanfm 
```

4. Dolphin (for Kubuntu)

```
 gksudo dolphin 
```

5. Nemo (for Linux Mint) - I believe it for Linux Mint Cinnamon Desktop

```
 gksudo nemo 
```  

Remember that whenever you open an app, file manager etc as sudo/root. You could delete, remove, change(anything) without prompt for permission and that will be dangerous. Better run gksudo(a window will pop-up to request you input the password and will tell you what app you will run). You can install gksudo(actually it's an app/feature for safety) if it's not available by run this -

```
 sudo apt-get install gksu 
```

Thanks.

---

