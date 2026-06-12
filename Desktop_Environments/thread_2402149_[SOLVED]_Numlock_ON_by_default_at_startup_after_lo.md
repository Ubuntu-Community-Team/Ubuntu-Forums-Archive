---
title: "[SOLVED] Numlock ON by default at startup after login in Lubuntu 18.04"
date: 2018-09-26
forum: Desktop Environments
---

### Post by MoebusNet on 2018-09-26
```
 sudo apt-get install numlockx 
```

I added numlockx to Default Applications in LXSession - Get to it via Menu > Preferences > Default Applications for LX Sessions.
When it comes up, select "Autostart" in the left panel. Then type "numlockx" into the empty box next to the [+Add] button, then click that +Add button. You'll see it show up in the list just above that.

I previously tried editing /etc/xdg/lubuntu/lxdm/lxdm.conf as root with leafpad -
Uncomment ```
 # numlock=0 
```
and make it ```
 numlock=1 
```
but it did not work.

I also previously tried -
```
 sudo su -
apt-get install numlockx
echo "/usr/bin/numlockx on" >> /etc/xdg/lxsession/Lubuntu/autostart 
```
which also failed to work.

Numlock ON at startup is working for me after login now.

---

