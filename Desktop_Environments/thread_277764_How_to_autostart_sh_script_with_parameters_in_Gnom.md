---
title: "How to autostart sh script with parameters in Gnome?"
date: 2006-10-15
forum: Desktop Environments
---

### Post by igor4u on 2006-10-15
How to autostart sh script with parameters in Gnome?
I have to type in terminal every day to open Internet session:
```
sh ~/gcauthcd_Linux/gcauthcd.sh start
```

Could you help me? ](*,)

---

### Post by ansi on 2006-10-15
> **igor4u said:**
> How to autostart sh script with parameters in Gnome?
I have to type in terminal every day to open Internet session:
```
sh ~/gcauthcd_Linux/gcauthcd.sh start
```
Could you help me? ](*,)

e.g.:

cat > ~/start_internet.sh
```
#!/bin/sh

sh ~/gcauthcd_Linux/gcauthcd.sh start
```
chmod +x ~/start_internet.sh

and create button on your desktop, which should execute your new script.

---

