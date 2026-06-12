---
title: "Kubuntu 14.10 Ctrl+Alt+F1 causes screen to go blank"
date: 2015-04-18
forum: Desktop Environments
---

### Post by mikeglaz on 2015-04-18
I need to install my Nvidia driver.  In order to do that I need to stop X server.  Stopping X server ```
sudo service lightdm stop
``` makes my screen go blank.  Trying Ctrl-Alt-F1 first makes my screen go blank as well.  All I can do in both scenarios is a hard reboot.

---

### Post by buzzingrobot on 2015-04-18
You should see a blank screen with a prompt in the upper left.  Try ctrl-alt-f2, and the rest of the functions keys.

If you're OK with the driver offered by the Driver Manager aka Additional Drivers, you don't need to jump through those hoops.

---

### Post by mikeglaz on 2015-04-18
Found this:

```

sudo sed -i -e 's/#GRUB_TERMINAL/GRUB_TERMINAL/g' /etc/default/grub
sudo update-grub

```

---

