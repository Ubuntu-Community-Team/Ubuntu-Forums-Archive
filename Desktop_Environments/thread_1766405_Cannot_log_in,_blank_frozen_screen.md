---
title: "Cannot log in, blank frozen screen"
date: 2011-05-24
forum: Desktop Environments
---

### Post by etienne@Rofti on 2011-05-24
Hi there!

I have Ubuntu 11.04 installed (from a clean install, did not upgrade from 10.10) on an HP Compaq 615, using the generic graphics driver, not the available proprietry one.

Today, suddenly, I cannot log in. When the login screen (GDM) comes up, and I try to log in to a Unity session, the screen goes blank (or sometimes has lines) and my computer does nothing. I have to hard-shutdown the computer by holding the power button in.

At first, I could fix this by logging in to the Classic or Classic (No Effects) environments but now, even that will not work. Does that mean it is a problem with X?

If anyone has any suggestions as to why this happens and how to fix it, I would be very grateful

Thanks

Etienne

---

### Post by Krytarik on 2011-05-24
Maybe you should try the proprietary driver then.

Btw., what is it, Nvidia or ATI/AMD?

And what exact model?

---

### Post by etienne@Rofti on 2011-05-25
Hi Krytarik

Thanks for the answer. I do not even know how to try the proprietry driver from the command line.

My laptop uses one of those built-in ATI/AMD chipset graphics cards. I'm not sure of the exact chip, but the HP website tells me it's an ATI Radeon&#8482; HD 3200.

Perhaps I should try to Google for some command-line help.

Thanks

E

---

### Post by Krytarik on 2011-05-25
Try booting into "recovery mode" to get to a working desktop.

Then install/activate the proprietary driver via "System -> Administration -> Additional Drivers".

You can also run the so-called "jockey" at the command line:
[http://askubuntu.com/questions/6521/how-can-i-reconfigure-the-nvidia-proprietary-drivers-from-the-command-line-ssh/11464#11464](http://askubuntu.com/questions/6521/how-can-i-reconfigure-the-nvidia-proprietary-drivers-from-the-command-line-ssh/11464#11464)

Another method is to install the driver manually:
```
sudo apt-get install fglrx
```

---

