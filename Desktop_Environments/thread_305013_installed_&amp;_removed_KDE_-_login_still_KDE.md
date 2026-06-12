---
title: "installed &amp; removed KDE - login still KDE"
date: 2006-11-22
forum: Desktop Environments
---

### Post by HereInOz on 2006-11-22
Hi All,

Running Ubuntu 6.06.  I thought I would have a play with the Kubuntu desktop, so installed it and didn't particularly like it, so I removed it again.

The trouble is, I still have the Kubuntu startup, login and logout screens, which then loads gnome.  I have re-installed the ubuntu desktop, but still the KDE start and login screens persist.  

What is it that I need to remove and install to get back to the Ubuntu startup, logon & logout screens?  I have tried using the "login window" option in system > administration, but it refuses to start after I enter the password, probably due to the different login window in use.

I hope you can help.  This is not serious, just one of those "I wish I hadn't done that" type of moments, which I would like to fix.

Cheers,

Alan

---

### Post by Zamboniman on 2006-11-22
```
sudo dpkg-reconfigure gdm
```

Select gdm rather than kdm as your display manager.

---

### Post by szegey on 2006-11-22
Change the login-screen:

```
sudo dpkg-reconfigure kdm
```

Edith: I'm so slow :)

---

### Post by HereInOz on 2006-11-23
Thanks good people - that is what I love about this system; there is always someone who will help out.  

That is fixed now.  We still get Kubuntu showing during the boot up process, but we can happily live with that.  Just that some people here didn't like the way that KDE shut down and had a bit of a complain about it.  Thanks again for helping me solve it.

---

