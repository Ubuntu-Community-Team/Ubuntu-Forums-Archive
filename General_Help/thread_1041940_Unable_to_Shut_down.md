---
title: "Unable to Shut down"
date: 2009-01-17
forum: General Help
---

### Post by xsilvergs on 2009-01-17
Hi,

This only started last night but is still happening this morning (17-01-09).

When I select Shut Down my PC shuts down normally, then after a couple of seconds it reboots itself. If I hibernate it, it hibernates until I wake it.

To my knowledge I haven't changed anything and only the regular updates have been done.

Any ideas where to look or how to rectify?

Thanks

Tony

---

### Post by cmnorton on 2009-01-17
Is your computer a laptop?

How are you shutting down your computer, menu or command line?

---

### Post by linux_tech on 2009-01-17
If you want to reboot type:
```
sudo reboot
```
```
sudo init 6
```

This solution sometimes resolves shutdown issues - [http://ubuntuforums.org/showpost.php?p=1722087&postcount=13](http://ubuntuforums.org/showpost.php?p=1722087&postcount=13)

---

### Post by xsilvergs on 2009-01-24
cmnorton

No it's a Desktop.

Today (a week later) I put it into Hibernation and it restarted about 2 seconds later. The only way to switch it off is to select shut down and as it goes off I switch it off at the mains before it reboots.

Thanks for any help you can give.

---

### Post by xsilvergs on 2009-02-01
Bump. Still can't shut down.

---

### Post by xsilvergs on 2009-03-05
Installing the Server Kernel cured it.

---

