---
title: "Azureus won't upgrade"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Tosa on 2006-08-22
Hi everybody!

Azureus 2.4.0.2  doesn't upgrade on my mashine!?
The updater detects new version (2.5.0), downloads it, installs it, but after restart it is still 2.4.0.2 and the updater detects new version again, downloads it, installs it...

I've tried manually downloading the latest Azureus package, and replacing the old azureus2.jar with the new one, but no go. it is still 2.4.0.2 trying to upgrade to 2.5.0...


Does anybody have any ideas?

---

### Post by masnevets on 2006-08-22
Is this Azureus you downloaded from the homepage or installed through synaptic?

---

### Post by Tosa on 2006-08-22
I downloaded it from the Azureus homepage. I've extracted only azureus2.jar and replaced the old one.

Well, I probably should uninstall the old one and install the new version. But I do find this rather weird, and I'd really would like to know if it could be fixed...

---

### Post by masnevets on 2006-08-22
That is pretty odd. Deleting your azureus directory and doing a download of the whole 2.5 tarball should fix it.

---

### Post by ykpaiha on 2006-08-22
if as an automatix user , it is tnstalled in /opt/azureus, just in a console make :
sudo chmod -R 777 /.where ever it is./
this should fix the dowload /update prob
++

---

### Post by babwe on 2006-08-22
ykpaiha that works fine m8 howdo I set sudo chmod -R 777 /.where ever it is./
back to what it wazz, or can I safely let it stay
thx

---

### Post by masnevets on 2006-08-23
-R 777 just means everyone can read/write/execute the contents of the folder. That shouldn't bring up any problems. I don't think there's a quick way to revert things back, as different files in the folder had different permission settings, so you'd have to do a lot of things individually.

---

### Post by Tosa on 2006-08-23
Thanks ykpaiha,

ubfortunatelly it didn't help...

---

