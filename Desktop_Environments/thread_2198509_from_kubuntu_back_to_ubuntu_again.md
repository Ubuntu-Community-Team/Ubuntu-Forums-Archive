---
title: "from kubuntu back to ubuntu again"
date: 2014-01-09
forum: Desktop Environments
---

### Post by nebula12 on 2014-01-09
hello!

i have ubuntu 12.04 with a gnome desktop and i wanted to try kubuntu desktop so i installed it from the command line
then i decided that it is not for me for the time being so i unistalled it
the problem is that the splash screen (log in screen) and the boot screen are still with a kde environment
what should i do to completely return to ubuntu and leave kubuntu?

---

### Post by xeonix on 2014-01-09
Reconfigure your display manager.

```
sudo dpkg-reconfigure gdm
```

---

### Post by zombifier25 on 2014-01-09
To revert from KDM back to LightDM, run this command at the command line:
```
sudo dpkg-reconfigure lightdm
```
Then choose LightDM.

For your boot screen, run this command:
```
sudo update-alternatives --config default.plymouth
```
Type the number corresponding to the ubuntu-logo theme.
Finally, apply the change:
```
sudo update-initramfs -u
```

---

### Post by nebula12 on 2014-01-09
```
Package `gdm' is not installed and no info is available.Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: gdm is not installed
```

this is what i get from the [COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg-reconfigure gdm
i will now try the others that u told me[/FONT][/COLOR]

---

### Post by xeonix on 2014-01-09
You can install it by:
```
sudo apt-get install gdm
```

Select "gdm" from the next screen. :]

---

### Post by zombifier25 on 2014-01-09
> **xeonix said:**
> You can install it by:
```
sudo apt-get install gdm
```

Select "gdm" from the next screen. :]

He was probably using LightDM before, since if he used GDM and then switched to KDM, GDM should have been installed.

---

### Post by nebula12 on 2014-01-09
i reverted to kdm when i switched to kde. now i am back to lightDM, thanks
i think everything is fine now with what u gave me zombifier25, only the boot screen is still grey and not purple but that's not a big deal since the log in screen is back to ubuntu
can i somehow uninstall everything that was installed with the kubuntu desktop installation? thank u all!!

---

### Post by xeonix on 2014-01-09
> **zombifier25 said:**
> He was probably using LightDM before, since if he used GDM and then switched to KDM, GDM should have been installed.

correct me if I am wrong, default gnome environment use's LightDM or GDM, as the OP said he was using gnome Desktop. :]

---

### Post by nebula12 on 2014-01-09
i think you're right but i probably used LightDM before installing kde. any idea how can i uninstall things that were installed with kde environment?
thnak u for your help!!

---

### Post by PJs Ronin on 2014-01-09
I have found Psychocat's tutorials most helpful in the past.   You might try the bottom of this [page]("http://www.psychocats.net/ubuntu/kde").

---

### Post by nebula12 on 2014-01-09
thank u, i'll try
those psychocats are awesome!!!

---

