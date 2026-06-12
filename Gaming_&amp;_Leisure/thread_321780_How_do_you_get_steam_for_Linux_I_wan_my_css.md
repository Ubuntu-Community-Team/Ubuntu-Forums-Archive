---
title: "How do you get steam for Linux? I wan my cs:s"
date: 2006-12-19
forum: Gaming &amp; Leisure
---

### Post by holdinout on 2006-12-19
How do you go about getting steam for Xubuntu?

---

### Post by holdinout on 2006-12-19
How do you go about getting steam for Xubuntu?

---

### Post by K.Mandla on 2006-12-19
(Merged threads. ;) )

---

### Post by hans-jakob on 2006-12-19
**1. First you need to install Wine on your computer.**

Add the following line to the file ”/etc/apt/sources.list”:
```
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
```

Then open a console and write:
```
sudo apt-get update
```

and:
```
sudo apt-get wine
```
This will update your repository database, and install wine.

Then you just need to create a wine directory in your home folder. This can be done by writing:
```
wine joo.exe
```
in the console. (Don't worry about the error message)

**2. After wine is install, you need to get the tahoma font.**

Write:
```
wget http://www.webpagepublicity.com/free-fonts/t/tahoma.ttf
```

And then:
```
mv tahoma.ttf ~/.wine/drive_c/windows/fonts/
```

**3. At last, you need to get steam, and install it.**

Write:
```
wget http://steampowered.com/download/SteamInstall.exe
```

And:
```
Wine SteamInstall.exe
```

If the steam update stops at 26%, you just write:
```
cd ~/.wine/drive_c/Program\ Files/Steam/
```

and:
```
wine steamTmp.exe SelfUpdate "Steam.exe" 14
```

Now you should have a working Stream installed.

I hope this helps :) 
/Hans

---

### Post by holdinout on 2006-12-19
Thanks Hans! I'll give it a try now...

---

### Post by holdinout on 2006-12-19
htt://www.webpagepublicity.com/free-fonts/t/tahoma.ttf: Unsupported scheme.

---

### Post by hans-jakob on 2006-12-19
> **holdinout said:**
> htt://www.webpagepublicity.com/free-fonts/t/tahoma.ttf: Unsupported scheme.

You missed a "p" in that protocol. It's
```
wget http://www.webpagepublicity.com/free-fonts/t/tahoma.ttf
```

---

