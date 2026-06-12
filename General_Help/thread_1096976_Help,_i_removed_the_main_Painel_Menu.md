---
title: "Help, i removed the main Painel Menu"
date: 2009-03-15
forum: General Help
---

### Post by fox_1 on 2009-03-15
Hi, i removed the main Painel Menu where i go to Aplications, Locals and System. 
Does anyone know how to make it visible again?
It is realy hard without it.

Thank you very mutch

---

### Post by geirha on 2009-03-15
Right click the panel -> Add to panel... -> choose Menu Line (or something like that, it's got the ubuntu icon infront of it)

Another option is to reset the panels to default by hitting Alt+F2 and running:
```
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by drs305 on 2009-03-15
And once you have the panels set the way you want them, you can save them with the following. The example saves the output to a file named *panels* on your Desktop:
```
gconftool-2 --dump /apps/panel > **~/Desktop/panels**
```

To restore saved panel settings and refresh the panel (example from file ~/Desktop/panels) :
```
gconftool-2 --load **~/Desktop/panels** && killall gnome-panel
```

---

### Post by fox_1 on 2009-03-15
Thank you, i will try to recover it with these informations. 

And also thanks for the tipp to save it, that is realy usefull.:)

---

### Post by shawfield on 2009-03-23
I've tried using the 'set to default' option, but whilst it works, within 2 seconds & before it can be 'saved', the original settings are restored.

Any thoughts ?

---

### Post by fox_1 on 2009-04-10
Than you, it worked realy fine.
):P

---

### Post by Lostin60's on 2009-04-10
> **geirha said:**
> )

Another option is to reset the panels to default by hitting Alt+F2 and running:
```
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel
```

Same problem. But alt>f2 doesnot work.  If I boot into restore and get a root prompt and try 
```
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel
```
I get "--recursive not recognized" I tried it with -R to no avail.  It also tells me 
```
gnome-panels
```
is not a command.  Help...lol.

---

### Post by geirha on 2009-04-11
> **Lostin60's said:**
> Same problem. But alt>f2 doesnot work.  If I boot into restore and get a root prompt and try 
```
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel
```
I get "--recursive not recognized" I tried it with -R to no avail.  It also tells me 
```
gnome-panels
```
is not a command.  Help...lol.

Did you uninstall something just before you lost the panels? This commonly happens when uninstalling evolution. Evolution is integrated with gnome, so when you uninstall it, it also uninstalls certain parts of gnome. One of which is gnome-panel. If this is the case, go into recovery mode and install ubuntu-desktop
```
aptitude install ubuntu-desktop
```

---

### Post by chageman on 2009-04-11
I too have lost my main panels, but cause is probably the uninstall of evolution mail as noted - however when running command suggested "aptitude install ubuntu-desktop" get error message "could not open lock file /var/lib/dpkg/lock - open )13 Permission denied" then unable to lock the administrative directory )/var/lb/dpkg/), are you root?"

Was having problems configuring evolution mail and decided to uninstall and reinstall when problem arose

also had cleaned up menu.lst entries so only Juanty version and Windows 7 version show at start up menu - not sure how to recover back up to run in safe mode?

thx for help in advance

---

### Post by geirha on 2009-04-12
> **chageman said:**
> I too have lost my main panels, but cause is probably the uninstall of evolution mail as noted - however when running command suggested "aptitude install ubuntu-desktop" get error message "could not open lock file /var/lib/dpkg/lock - open )13 Permission denied" then unable to lock the administrative directory )/var/lb/dpkg/), are you root?"

You need to run it as root, so if you're not in a root shell (as you get when you boot in recovery mode), you'll need to prepend the command with sudo.

```
sudo aptitude install ubuntu-desktop
```


> **chageman said:**
> 
Was having problems configuring evolution mail and decided to uninstall and reinstall when problem arose

also had cleaned up menu.lst entries so only Juanty version and Windows 7 version show at start up menu - not sure how to recover back up to run in safe mode?

thx for help in advance

If you have problems configuring a program, a reinstall will almost never have any effect. In the case of evolution, the configuration is stored in a hidden folder in your homefolder; ~/.evolution. If you delete that folder, all settings will be set back to default.

---

