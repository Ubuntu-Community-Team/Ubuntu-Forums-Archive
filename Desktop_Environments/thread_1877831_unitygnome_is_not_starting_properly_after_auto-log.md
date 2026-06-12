---
title: "unity/gnome is not starting properly after auto-login"
date: 2011-11-08
forum: Desktop Environments
---

### Post by fcarramate on 2011-11-08
Hi,

found today a big pain in my laptop!

[COLOR="Green"]Symptoms:[/COLOR]
After successful update my ubuntu more concretely unity was not starting properly.
What i saw was the left and upper bar not appearing. [Alt] + [F2], [CTRL] + [ALT] + [BACKPSPACE],were not sorting any effect.



[COLOR="Red"]Problem description:[/COLOR]
Personally, I use auto-login which is cool since it allows me to launch the application defined at "Startup Applications".

One of those applications is:
```
/usr/bin/gnome-screensaver-command --lock
```

the "system" breaks with the sequence: auto-login and screen lock.




[COLOR="Blue"]Solution:[/COLOR]
press [CTRL] + [ALT] + [F1]
login with your user and password

the following command will disable your Startup Applications"
```
sed -i '/X-GNOME-Autostart-enabled/s/true/false/' ~/.config/autostart/*.desktop
```

now just reboot the machine
```
sudo reboot
```

instead of rebooting a **more elegant** way is to restart gnome
```
sudo /etc/init.d/gdm restart
```

---

