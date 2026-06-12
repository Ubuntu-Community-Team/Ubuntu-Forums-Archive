---
title: "Removing traces of Kubuntu - help please"
date: 2006-09-13
forum: Desktop Environments
---

### Post by rshd301 on 2006-09-13
I had installed KDE on my Ubuntu system a few dyas ago to see what it was like. Ever since, I have the Kubuntu startup display in the wrong resolution and would like to revert back to the Ubuntu one as I have decided to remain with Gnome.

I apologise for not using the correct terminology for this screen but it's the one which is brown text on a black screen and displays the startup processes as they happen giving an OK or FAIL result.

As I said, I would like to revert to the Ubuntu screen with a resolution of 1280x1024. Can anyone advise please ???

---

### Post by xyz on 2006-09-13
I don't know how you installed it so...it depends:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
Let us know.

---

### Post by ayoli on 2006-09-13
in a terminal, type in:
```
sudo apt-get remove kubuntu-desktop
```
then
```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---

### Post by rshd301 on 2006-09-13
Tried as you suggested but no luck.

Can you advise what the correct name is for this screen ?

---

### Post by ayoli on 2006-09-13
you may try:
```
sudo apt-get remove kubuntu-artwork-usplash
```
and
```
sudo dpkg-reconfigure usplash
```

---

### Post by zba78 on 2006-09-13
> **rshd301 said:**
> Tried as you suggested but no luck.

Can you advise what the correct name is for this screen ?

The correct name for it is a Splash Screen

---

### Post by rshd301 on 2006-09-13
Many thanks. I have now returned to the Ubuntu usplash.

Sorry to be a pain in the rear but any ideas as to how to change its resolution. It's way too big.

---

### Post by xyz on 2006-09-13
Change resolution...great HowTo:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

