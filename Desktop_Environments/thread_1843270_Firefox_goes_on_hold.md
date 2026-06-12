---
title: "Firefox goes on hold"
date: 2011-09-13
forum: Desktop Environments
---

### Post by PaulNL on 2011-09-13
Hello all,

When i use firefox to display a website with flash, Firefox goes in freeze after about 1.5 hours. What can i do so firefox stay running ???

I have read on the internet something about a Xorg bug but i did not find the solution


Paul

---

### Post by Frogs Hair on 2011-09-13
Are you running 9.04 as your user information indicates ? Please post your Ubuntu , Firefox , and Flash version . If you are running an old version of Firefox and Flash it may be part of the problem .

---

### Post by PaulNL on 2011-09-14
I use Ubuntu 11.04 with firefox 6.0  better to say i have the system all updated.

---

### Post by drawkcab on 2011-09-14
If you are running 64bit natty then make sure you install the 64bit flash beta.

```
sudo add-apt-repository ppa:sevenmachines/flash
sudo apt-get update
sudo apt-get install flashplugin64-installer
```

---

### Post by PaulNL on 2011-09-14
The machine runs a 32 bit version. The strange thing is He hangs after about 1.5 hours

---

### Post by Frogs Hair on 2011-09-14
Try this add-on , it automatically installs the latest correct version of Flash with an option to try Betas as well . I'm not sure what else to try if it is a flash related problem . [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

