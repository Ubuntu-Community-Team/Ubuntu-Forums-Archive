---
title: "Unity Desktop fails to load"
date: 2023-01-06
forum: Desktop Environments
---

### Post by ScottyK7 on 2023-01-06
Greetings!
I have a fresh install of Ubuntu 20.04.1 on a laptop. I went to the terminal and installed Unity. 
```
sudo apt-get install unity
```
Upon rebooting, I logged in and selected the "unity" desktop. After logging in I get a full screen error message stating that "A problem has occurred, and the system can't recover. All extensions have been disabled as a precaution". The only option is to log back out. If I log into Ubuntu with the default desktop, everything is fine.

I know since it's a fresh install I can just install Unity from the start, but I was wondering if there is anything I can do to get Unity working, without having to reinstall.

---

### Post by deadflowr on 2023-01-06
Try installing unity with
```
sudo apt install ubuntu-unity-desktop
```

If that doesn't work based on 
> A problem has occurred, and the system can't recover. All extensions have been disabled as a precaution
This might be an issue with not having the package dbus-x11 installed so maybe try installing it
```
sudo apt install dbus-x11
```

---

### Post by ScottyK7 on 2023-01-06
That did it! After rebooting the machine I got a fatal error. I went into the console mode (Ctrl+Alt+F3) installed dbus-x11, and rebooted. Upon logging it the system is up and running. Thanks!!

---

