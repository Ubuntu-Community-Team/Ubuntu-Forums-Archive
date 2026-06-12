---
title: "Screen turns off"
date: 2009-05-09
forum: General Help
---

### Post by mmeisam on 2009-05-09
Hello,

I recently upgraded to 9.04 and am now having this weired problem where after a little while of using the computer the screen just shuts off and i have to do a hard reboot to get it going again, any ideas on what it could be. Sorry I just moved over from windows, trying to get used to Ubuntu.

Thanks,
Meisam

---

### Post by pastalavista on 2009-05-09
Open a terminal in System->Applications->Terminal and enter this
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and reboot... if that doesn't work, try rebooting in recovery mode and select repair xorg, or something like that... last on the list

---

### Post by mmeisam on 2009-05-10
Ok, so i did that and it worked but now i have a new problem. Instead of the screen turning off the computer just freezes randomly, any ideas?

Thanks,
Meisam

---

### Post by pastalavista on 2009-05-10
That's a bug in the new kernel on some machines. I never had that problem so couldn't say how to fix it. Have you tried searching the forum? That's what I do when something doesn't work right and usually someone else here has had the same problem.

---

### Post by mmeisam on 2009-05-10
I have been looking around for the past few days and have not really been able to find anything on this. This is what messages.log says right when it crashes:

```
May  9 22:18:35 meisam-desktop kernel: [   26.272592] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  9 22:18:42 meisam-desktop kernel: [   33.371834] warning: `proftpd' uses 32-bit capabilities (legacy support in use)
May  9 22:18:44 meisam-desktop kernel: [   34.626140] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  9 22:38:25 meisam-desktop -- MARK --
May  9 22:58:25 meisam-desktop -- MARK --
May  9 23:18:25 meisam-desktop -- MARK --
May  9 23:38:25 meisam-desktop -- MARK --
May  9 23:42:38 meisam-desktop syslogd 1.5.0#5ubuntu3: restart.
May  9 23:42:38 meisam-desktop kernel: Inspecting /boot/System.map-2.6.28-11-generic
May  9 23:42:39 meisam-desktop kernel: Cannot find map file.
May  9 23:42:39 meisam-desktop kernel: Loaded 53960 symbols from 47 modules.
```

I'm not sure if there is anything wrong over here, any help will be really appreciated.

Thanks,
Meisam

---

### Post by pastalavista on 2009-05-10
Check out launchpad.net (link at top of this page). That's where you should report bugs like this and your best bet for finding the solution.

---

### Post by mmeisam on 2009-05-18
Well i posted on launchpad and no one has answered my question, im still having this problem. [https://answers.launchpad.net/ubuntu/+question/70870](https://answers.launchpad.net/ubuntu/+question/70870)

Thanks,
Meisam

---

