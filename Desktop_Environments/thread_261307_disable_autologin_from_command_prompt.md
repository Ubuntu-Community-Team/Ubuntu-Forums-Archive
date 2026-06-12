---
title: "disable autologin from command prompt"
date: 2006-09-20
forum: Desktop Environments
---

### Post by Hiroshima on 2006-09-20
I'd like to disable the automatic login from the comand prompt, for the reasons I wrote about here:

[http://ubuntuforums.org/showthread.php?t=260739](http://ubuntuforums.org/showthread.php?t=260739)

That would allow me to choose KDE or Gnome each time I loggin, rather than automatically get directed to Gnome (which isn't working at present).

I'd like to get into KDE which was working the last time I used it, and then when I have a system I can use, then I'll try to fix Gnome (watch for my questions later).

Thanks in advance,

Hiroshima

---

### Post by mssever on 2006-09-20
I don't know how to disable the default login, but you can switch to KDM (KDE's login manager) instead of GDM.
```
sudo nano /etc/X11/default-display-manager
```Note the current contents of the file for later restoration and insert the path to kdm (whereis kdm). Install KDM if necesary.
```
sudo /etc/init.d/gdm stop && sudo /etc/init.d/kdm start
```

---

### Post by Hiroshima on 2006-09-21
Mssever, thanks for the advice.  I gave it a try, and on the second command,
> sudo /ect/init.d/gdm stop && sudo /etc/init.d/kdm
I got an error stating that stop was not a command...
anyhow, I got frustrated enough to "sudo aptitude remove ubuntu-desktop" ... and after that both Gnome and KDE seem to be working properly ( I thought Gnome would be gone... but hey, it's working for now...)

Thanks for the ideas anyhow,

Hiroshima

---

### Post by mssever on 2006-09-21
> **Hiroshima said:**
> Mssever, thanks for the advice.  I gave it a try, and on the second command,

I got an error stating that stop was not a command...
anyhow, I got frustrated enough to "sudo aptitude remove ubuntu-desktop" ... and after that both Gnome and KDE seem to be working properly ( I thought Gnome would be gone... but hey, it's working for now...)

Thanks for the ideas anyhow,

Hiroshima

Must have mis-typed something... But, I'm glad that you got it working. That shouldn't have worked! :D

I would advise re-installing ubuntu-desktop, though. Your system will work perfectly without it, but if any packages are ever added to the Ubuntu desktop, you probably won't know about it without that package.

---

### Post by Hiroshima on 2006-09-22
Makes sense, will do it now.  Cheers, and thanks for the help.

Hiroshima

---

