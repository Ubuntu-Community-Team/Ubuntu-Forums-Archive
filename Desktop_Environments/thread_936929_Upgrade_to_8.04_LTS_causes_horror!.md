---
title: "Upgrade to 8.04 LTS causes horror!"
date: 2008-10-03
forum: Desktop Environments
---

### Post by alphis on 2008-10-03
Hey guys. Last night I upgraded my laptop (which hadn't been upgraded in a while) to 8.04 using the typical update manager. After about 1-2 hours it finished and then restarted. After the reboot I get the gdm login for gnome as usual but it looks prettier. Here's where the problem comes in.

I login, and the desktop never loads. Instead I see a small white box in the upper left corner of the screen and thats it. Small white box in left top and light brown everywhere else and nothing happening.

Any ideas? I'd like to salvage this install but if I cannot I will have to do a full new install with 8.04. I have remote access to the machine now, hoping there will be a solution I can apply via cmd line. Any help is appreciated!

Thanks.

---

### Post by sayakb on 2008-10-03
Press Ctrl+Alt+F1 , login and do:
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

