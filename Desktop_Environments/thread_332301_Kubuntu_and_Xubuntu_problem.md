---
title: "Kubuntu and Xubuntu problem"
date: 2007-01-05
forum: Desktop Environments
---

### Post by wersdaluv on 2007-01-05
After installing Xubuntu on top of Kubuntu and Ubuntu, my Kubuntu had problems. The wallpaper was changed, the splash screen was changed, the KDE panel was lost, and lots of other stuff. Also there was a beneficial effect as Ubuntu got faster (I don't know why).

When I tried to use Xubuntu, the Xfce session was unavailable so I just decided to fix my Kubuntu. I uninstalled and reinstalled Kubuntu. Some problems were solved. I had some KDE apps working again, my splash screen was back, my Kubuntu wallpaper was back, etc. But the KDE panel was still lost and Kontact got buggy (the BasKet icon and KOrganizer icons sometimes appear somewhere outside the taskbar). Also, I already found the Xfce desktop environment in the session types tab but when I ran Xfce, there was also no panel. 

How can I fix this?

Thanks in advance. :)

---

### Post by Pobega on 2007-01-05
Are these all on seperate partitions or are you replacing previous installs each reinstall?

---

### Post by wersdaluv on 2007-01-05
> **Pobega said:**
> Are these all on seperate partitions or are you replacing previous installs each reinstall?

This is in one partition and I'm trying to replace previous installs

---

### Post by Pobega on 2007-01-05
Are you using CD installs or Aptitude to switch between Kubuntu/Xubuntu?

---

### Post by wersdaluv on 2007-01-06
I'm using aptitude

---

### Post by Pobega on 2007-01-08
> sudo -i
aptitude remove ubuntu-desktop
aptitude remove kubuntu-desktop
aptitude remove xubuntu-desktop
aptitude install <desktop of choice>
exit

Sorry it took so long to respond.

---

