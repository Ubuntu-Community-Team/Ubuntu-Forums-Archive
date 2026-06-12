---
title: "Wine - Most recent version for 5.10"
date: 2006-03-13
forum: Desktop Environments
---

### Post by stabface on 2006-03-13
I have ben trying to install WINE, and I found several how-tos but They are all out dated. Can anyone point me to the most upto date way t get wine running?

---

### Post by kaamos on 2006-03-13
Here is a quick solution:

Applications->Accessories->Terminal
```
sudo su
cp /etc/apt/sources.list /etc/apt/sources.list.bak
echo "deb http://wine.sourceforge.net/apt/ binary/" >> /etc/apt/sources.list
apt-get update
apt-get install wine
exit
wine *name_of_windows_file*.exe
```

---

### Post by stabface on 2006-03-13
What about Winetools?

---

### Post by kaamos on 2006-03-13
I don't think there are winetools for the beta (0.9.x) versions of wine. Use "winecfg" to configure.

---

### Post by stabface on 2006-03-13
ok cool i will try it out and post if i have any problems

---

