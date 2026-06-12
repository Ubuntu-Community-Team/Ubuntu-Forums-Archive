---
title: "Installing shell extensions"
date: 2012-01-25
forum: Desktop Environments
---

### Post by rajohns08 on 2012-01-25
[http://intgat.tigress.co.uk/rmy/extensions/index.html](http://intgat.tigress.co.uk/rmy/extensions/index.html)

i have 11.10 so i downloaded gnome-shell-frippery-0.3.6.tgz

i used tar -zxvf gnome-shell-frippery-0.3.6.tgz

now i'm stuck. what do i do now? it says the extensions will be placed in ~/.local/share/gnome-shell/extensions but how do i get to this location? and what do i click once i'm there?

---

### Post by pbrane on 2012-01-25
Unzipping the archive from your home directory will place the extensions in the correct directory. I assume you will have to log out and log back in to see the affects. I don't use GNOME anymore so I'm not sure. All the information is on the web site. You may have to delete any extensions you don't want. 

You can get to that location in nautilus by enabling hidden file viewing (CTRL-H ?). **~/.local** is a hidden directory in your hone directory.

---

### Post by stefangr1 on 2012-01-25
To change themes, you should install gnome-tweak-tool:
```
sudo apt-get install gnome-tweak-tool
```

After installing, this should show up as "Advanced Settings". There are several tabs to manage and install Gnome shell and shell extensions.

---

### Post by oldos2er on 2012-01-25
Thread moved to Desktop Environments.

---

