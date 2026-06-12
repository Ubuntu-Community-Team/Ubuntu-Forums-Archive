---
title: "Ctrl-Alt-Backspace does not work in Jaunty"
date: 2009-05-28
forum: General Help
---

### Post by crazyfuturamanoob on 2009-05-28
When I updated to Jaunty, ctrl-alt-backspace stopped working.

Now I have to force-shutdown the laptop by removing battery if I can't normally reboot. :(

---

### Post by Pessulus on 2009-05-28
first you have to install dontzap:
sudo apt-get install dontzap

then: 

sudo dontzap --enable

or 

sudo dontzap --disable

Where “disable” means that Ctrl+Alt+Backspace restarts the xserver while “enable” means that it won’t.

---

### Post by Therion on 2009-05-28
> **crazyfuturamanoob said:**
> When I updated to Jaunty, ctrl-alt-backspace stopped working.
It's a feature!

---

### Post by m_duck on 2009-05-28
Or you can use right alt + print screen + k I think.

---

### Post by mbeach on 2009-05-28
see:
[http://ubuntuforums.org/showthread.php?t=1167099&highlight=ctrl+alt+backspace](http://ubuntuforums.org/showthread.php?t=1167099&highlight=ctrl+alt+backspace)
or even better:
[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)

---

### Post by crazyfuturamanoob on 2009-05-29
Thanks, got it working.

> **Therion said:**
> It's a feature!

It was a feature.

---

### Post by binbash on 2009-05-29
[http://www.ubuntu-inside.me/2009/05/howto-enable-ctrlaltbackspace-on-ubuntu.html](http://www.ubuntu-inside.me/2009/05/howto-enable-ctrlaltbackspace-on-ubuntu.html)

---

### Post by ssully on 2009-11-01
Note for karmic users: use following method

- System > Preferences > Keyboard
- Layouts > Layout Options
- "Key sequence to kill the X server" > enable Ctrl+Alt+Backspace

cite: [http://www.ubuntugeek.com/how-to-enabledisable-ctrlaltbackspace-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-enabledisable-ctrlaltbackspace-in-ubuntu-9-10-karmic.html)

---

### Post by Andreas1 on 2009-11-01
i use alt+print+k now

---

