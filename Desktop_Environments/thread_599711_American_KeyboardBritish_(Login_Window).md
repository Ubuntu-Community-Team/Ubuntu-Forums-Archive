---
title: "American Keyboard/British (Login Window)"
date: 2007-11-01
forum: Desktop Environments
---

### Post by Fluxboxen on 2007-11-01
Hi All
I changed a few graphics settings via the gui (whilst trying to get my TV and monitor working)

However upon reboot it takes me to the login window and asks me for my username and password.

The only problem is here is that its changed my £ sign to a # sign (It appears to be an american keyboard layout)

I've logged into the guest user account that doesnt have admin rights and thats how I'm writing to you now.

However I cannot log into my primary account as the password has a pound sign in it.


Does anyone know how to change the keymap on the splash screen so its NOT US but GB,.

Thank you

---

### Post by Fluxboxen on 2007-11-01
Solved this,
For future referance incase this happens to anyone else

Boot into safe mode / command line and then type

nano /etc/X11/xorg.conf

Scroll down to input keyboard and change from 
us
to
gb

Solved,

---

