---
title: "Installed KDE, now can't use the system at all"
date: 2008-09-08
forum: Desktop Environments
---

### Post by blazemore on 2008-09-08
I thought I'd check out KDE 4.1.1, so I installed kubuntu-kde4-desktop (or whatever it is) on my Ubuntu system.
I set kdm-kde4 as my default window manager.
Now when my system boots up, KDE gives me an error message (something about  a greeter, doesnt matter), and when I OK it, I just get a blank screen. Ctrl+alt+backspace doesnt work, neither does Ctrl+Alt+F3 or whatever. I just want to get rid of KDE and kdm completely.

I removed recovery mode from my grub ages ago so I can't even get a command line!

---

### Post by kjohansen on 2008-09-08
Before you login you should be able to change your sessions to use GNOME or whatever other windows system you have, by clicking the sessions button on the log in screen.

The you can do this to get KDE and its apps gone:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Or are you saying the computer wont even boot to the login screen?

---

### Post by blazemore on 2008-09-08
I have autologin enabled. If I could somehow disable this, I could easiliy take it from there. Is there a way to do this?

---

### Post by benerivo on 2008-09-08
It's unusual not to even get a command line option. To stop auto login, i would load the ubuntu live cd if you have it, so you can edit one of the files on the system. If you can edit ```
/etc/X11/default-display-manager
``` then you can change the bit that says kdm, to read gdm. I think you might have to run ```
gksudo nautilus
``` from the live cd so that it allows you to open this file for editing.

When you reboot, it should try to load gdm instead. If you have it installed it will load it. What happens next depends on whether you had gdm set up to auto login or not. If you are unlucky, gdm may just autologin to kde and you're still stuck. If this is the case, then i would edit that file again and change it to a login manager that is not installed, such as wdm. Then it shouldn't load any desktop environment. From here you can ```
sudo apt-get install wdm
```and then start wdm with ```
sudo /etc/init.d/wdm start
```

---

### Post by slakkie on 2008-09-09
Boot into single user mode, then 

echo /usr/bin/gdm > /etc/X11/default-display-manager

You could also try to run dpkg-reconfigure gdm to reconfigure your display manager.

---

