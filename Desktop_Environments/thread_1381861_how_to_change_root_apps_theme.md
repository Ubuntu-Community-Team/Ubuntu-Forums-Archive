---
title: "how to change root apps theme"
date: 2010-01-15
forum: Desktop Environments
---

### Post by nerdy_kid on 2010-01-15
ok, so normaly in order to change root qt/gtk app's theme in KDE, i have to run kdesudo system settings.  I think it is possible via linking to have the root theme automaticly sync with my user theme, but i dont know which files to link.
Thanks in advance!

---

### Post by schnelle on 2010-01-15
Try with program gtk-chtheme.
```
sudo aptitude install gtk-chtheme
```
Then Alt+F2 and type kdesudo gtk-chtheme.

This helped me with synaptic in kubuntu. Synaptic theme was very ugly because it was running as root.

---

### Post by falconindy on 2010-01-15
Make a symlinks in /root to your own:

$HOME/.icons
$HOME/.themes

> **schnelle said:**
> This helped me with synaptic in kubuntu. Synaptic theme was very ugly because it was running as root.
I heard Synaptic runs slower when its unthemed.

---

### Post by nerdy_kid on 2010-01-16
thanks for the replies!

I need to link the configs for my QTcurve theme and the configs for my QT themes, as well as the config for KDE appearences (which sets the current QT theme).

???

where would i find those?

thanks.....

---

### Post by DocXcz on 2010-01-23
Hi,

for synaptic (and other gtk apps running as root), you have to edit sudoers file:

 1) Run ```
sudoedit /etc/sudoers
```
 2) Find line like this:
```
Default env_reset
```
	and change it to
```
Defualt env_keep = "GTK_RC_FILES GTK2_RC_FILES KDEDIRS GTK_MODULES"
```
 3) Save file.

Then create symlink to qtcurve config files from your home to root home:

```
sudo ln -s /home/your_name/.config/qtcurve /root/.config/
```

If you would like to have unified theme for KDE apps running as root, I haven't discovered yet any other way than link my .kde dir to /root/.kde :(

---

### Post by jegenph on 2010-09-01
thanks schnelle!

---

### Post by Brokensoul on 2011-11-02
Thanks, works perfectly with kubuntu 11.10 !

---

