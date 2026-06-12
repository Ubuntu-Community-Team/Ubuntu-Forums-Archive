---
title: "Unlock Root account and set X11"
date: 2006-01-07
forum: Desktop Environments
---

### Post by jaywatkins on 2006-01-07
Hi

I have an install of Kubuntu and I need to set the resolution above 640X480.  Ubuntu needs better video support, this is a four year old machine!  I cannot seem to save any Xorg settings I make because I do not have write access to the file.  In order to  grant myself access to the files, I need to log on as root.  I do not recall the setup program asking for root account configuration.  So, how does one log on as an unconfigured user?  

Thanks in advace (TIA)

- Jason Watkins

---

### Post by Mercurybird on 2006-01-07
Yeah I need to know also. I'm trying to install KDE into Ubuntu and everything is "so far so good" but its telling me that it can't open /etc/apt/sources.list because I don't have permission.

---

### Post by GeneralZod on 2006-01-07
The answer to all of life's questions are here:

[https://wiki.ubuntu.com//RootSudo](https://wiki.ubuntu.com//RootSudo)

:)

---

### Post by aysiu on 2006-01-07
```
sudo kwrite /etc/apt/sources.list
``` ```
sudo kwrite /etc/X11/xorg.conf
```

---

### Post by Mercurybird on 2006-01-07
Thank you! :p

---

