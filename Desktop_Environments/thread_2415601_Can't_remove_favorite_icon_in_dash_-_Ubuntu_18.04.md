---
title: "Can't remove favorite icon in dash - Ubuntu 18.04"
date: 2019-03-28
forum: Desktop Environments
---

### Post by andrecupini on 2019-03-28
Hello,
 my dash in the Ubuntu 18.04 desktop has a nautilus icon that can't be removed.

When righ-clicked it's show me **"Add to favorites" **instead **"Remove from favorites"**. 

Running the command:
```

# gsettings get org.gnome.shell favorite-apps 

```
the icon isn't in the array:
> 
['org.gnome.Terminal.desktop', 'google-chrome.desktop', 'jetbrains-idea-ce.desktop', 'jetbrains-phpstorm.desktop', 'atom.desktop', 'azuredatastudio.desktop', 'dbeaver.desktop', 'mysql-workbench.desktop', 'gnome-calculator_gnome-calculator.desktop', 'org.gnome.gedit.desktop', 'org.remmina.Remmina.desktop', 'skypeforlinux.desktop']

How can I remove this icon?

> 
PS: The app is not opened. Some bug have fixed the icon. If I open nautilus, two icons appears.


[ATTACH=CONFIG]282871[/ATTACH]   [ATTACH=CONFIG]282872[/ATTACH]

---

