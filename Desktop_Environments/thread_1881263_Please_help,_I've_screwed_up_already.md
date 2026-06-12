---
title: "Please help, I've screwed up already"
date: 2011-11-15
forum: Desktop Environments
---

### Post by baz.g on 2011-11-15
I have recently wiped my laptop which had Ubuntu 10.04 installed and installed 11.10. Everything was working perfectly, then I decide to try tweaking :(

I followed the directions on here: [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

and ran the command to make the lock screen work:
```

sudo ln -s /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command

```

I had previously installed the xscreensaver.

I also installed synaptic and CCSM but have since removed them to try and solve this problem.

I have also removed the symbolic link for the lock screen and removed xscreensaver.

I have also tried the unity and compiz reset commands at the bottom of the page but i still get the crappy screen shown in the attachment when i login i.e. no unity, or system, tray or anything (i have rebooted multiple times). the only way i can get to a web browser is using the terminal. 

i have tried logging out and logging in as a guest and that is fine, it is just this login. i have also tried logging in as this user as 2d and as normal and they are both the same.

please help :(

---

### Post by mswift on 2011-11-15
try deleting your compiz config.

```
cd
```
```
rm -rf .config/compiz-1/
```

Then retry ```
unity --reset
```

---

### Post by baz.g on 2011-11-15
you are a star! worked perfectly, thank you very much :)

---

