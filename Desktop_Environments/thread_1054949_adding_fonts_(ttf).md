---
title: "adding fonts (ttf)"
date: 2009-01-30
forum: Desktop Environments
---

### Post by raunhar on 2009-01-30
How do I install new fonts (ttf) in Ubuntu 8.10
The fonts are from winows fonts folder. I have takena backup and do not know,how to proceed.
Should I copy them directly to etc/fonts folder.
There are two sub folders in the etc/fonts folder (conf. avail , cont.d)

---

### Post by m_duck on 2009-01-30
If you want them available to anybody who uses the computer, copy the files into [COLOR=Red]/usr/share/fonts/truetype/msfonts[/COLOR]. You will need to create the msfonts folder, so either in nautilus as root (gksu nautilus) or in terminal```
sudo mkdir /usr/share/fonts/truetype/msfonts
```If you don't mind the fonts being just available for your user, make a [COLOR=Red].fonts[/COLOR] directory in your home folder if it does not already exist and move the .ttf files there.```
mkdir ~/.fonts
```

Finally, you need to refresh the font cache, so run the following from a terminal```
fc-cache -vf
```You MS fonts should now be ready to use.

---

