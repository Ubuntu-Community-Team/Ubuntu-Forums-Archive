---
title: "A normal user that cannot shutdown"
date: 2010-06-05
forum: Desktop Environments
---

### Post by narcisgarcia on 2010-06-05
I create a desktop user with an empty password running these terminal commands:
```
adduser --disabled-password --gecos "" myuser
MyPassword=""
Salt="12"
MyPassword="$(perl -e "print crypt('$MyPassword','$Salt');")"
usermod --password "$MyPassword" "myuser"
usermod --groups cdrom,audio,video,plugdev,fuse myuser
```

The new user opens a desktop session right (only selecting the username and pressing [Enter] when asked for password), but cannot shut down the computer and this is the problem.

When this user presses the shutdown button/option in the desktop bar, a confirmation dialog is shown, but after confirming nothing happens. The desktop session is still working as if cancelled the shutdown.

---

