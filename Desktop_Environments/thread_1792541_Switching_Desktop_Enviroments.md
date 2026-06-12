---
title: "Switching Desktop Enviroments"
date: 2011-06-28
forum: Desktop Environments
---

### Post by simolokid4 on 2011-06-28
Dear forums,

Recently installed ubuntu 11.04 and loved it. But since I wanted to see how minimal I could go I installed the lubuntu DE aswell.. worst mistake ever.

It worked and I got the desktop enviroment. Only since then whenever I try to login to ubuntu I get this error:

XSession: unsupported number of arguments (2); falling back to default session.

Simply logging into lubuntu keeps working. If i log into ubuntu I do get my old wallpaper + conky thing back but nothing else.. so basicly a hard reboot is needed because alt+f2 to bring up a terminal or whatever wont work either. Havent tested tty1-6 yet.

I'm about 5 houres away from reinstalling it all.. (prox time needed is like.. an houre tops and everything is back.)

Any help? Thanks

Did the following:
- sudo aptitude reinstall ubuntu-desktop
- synaptic package manager -> complete removal lubuntu, did its thing while i was logged into lubuntu. No errors, no effect.
- sudo aptitude remove ubuntu-desktop, sudo aptitude install ubuntu-desktop

Thus far; no effect. Still get the error.

---

### Post by mexicanseaf00d on 2011-06-28
I had similar problems once, deleting .xsession or .xinitrc in the home-dir helped me. However, I used these files to set up a custom session, so they might not exist for you

---

### Post by jerrrys on 2011-06-28
try this

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Krytarik on 2011-06-28
simolokid4, both "ubuntu-desktop" and "lubuntu-desktop" are [MetaPackages]("https://help.ubuntu.com/community/MetaPackages"), so removing or reinstalling them doesn't affect any "real" package.

So, to reinstall all dependend packages, you have to put it like this:
```
sudo apt-get purge ubuntu-desktop
sudo apt-get autoremove
sudo apt-get install ubuntu-desktop

```But this may not work in every case, depending on the state of the dependend packages.

Hope this still helps, after passing your 5 hours deadline. ;-)

---

