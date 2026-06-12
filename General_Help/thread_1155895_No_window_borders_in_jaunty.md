---
title: "No window borders in jaunty"
date: 2009-05-11
forum: General Help
---

### Post by rrajath on 2009-05-11
Hi.. I installed compizconfig-settings-manager recently. When I enabled the Blur Windows effect, the screen went blank. I restarted the system, yet the screen used to go blank immediately after login. Somehow, I solved this problem by going to failsafe terminal and removing compiz-core. The problem was solved but now I'm not getting window borders at all. Alt+Tab isn't working either.

---

### Post by hw-tph on 2009-05-11
First open a terminal window (or hit Ctrl+Alt+F1 for a text login window) and remove or move your ~/.compiz directory: **mv ~/.compiz ~/.compiz-old**. This should take care of your messed up settings. Then reinstall compiz or just compiz-core (the compiz package depends on compiz-core so it would install compiz-core and everything else that you need).

---

### Post by rrajath on 2009-05-11
I did exactly the same thing you mentioned. Renamed the compiz directory and reinstalled compiz-core. But it isn't working. When I goto System > Preferences > Windows, it says 'Window manager "compiz" has not registered a configuration tool'.

---

### Post by adaniels on 2009-05-11
I have the same issue. A thing that I'm noticing is that "Visual Effects" in "Appearance Preferences" is always set to "None" after a reboot, even when "Normal" is selected. After selecting "Normal" manualy, windows borders, keyboard short-keys, etc work again. Removing ~/.compiz and reinstalling all compiz packages did not solve the issue.

The behaviour after reboot (or login/logout) looks similar to disabling all compiz modules in the compiz configuration editor. Compiz didn't complain to the syslog.

---

### Post by adaniels on 2009-05-11
Follow up: Compiz is not running after reboot.
```

arnold@arnold-laptop:~$ ps aux | grep compiz
arnold    6850  0.0  0.0   3336   808 pts/0    S+   21:31   0:00 grep compiz

```

After starting compiz manually in a terminal with `/usr/bin/compiz --replace`, everything is working. As a workaround, I've added the command "/usr/bin/compiz --replace" in 'Startup applications'.

Does anyone know what's going wrong? A proper fix would be pleasant.

---

### Post by adaniels on 2009-05-14
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/348432](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/348432)

---

