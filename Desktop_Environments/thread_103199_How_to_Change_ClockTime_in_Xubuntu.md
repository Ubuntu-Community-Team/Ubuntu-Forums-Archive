---
title: "How to Change Clock/Time in Xubuntu?"
date: 2005-12-13
forum: Desktop Environments
---

### Post by Gadren on 2005-12-13
I'm loving Xubuntu, but the clock is set to the wrong time.  How do I change it?  There doesn't seem to be a setting for it.

---

### Post by Ampersand on 2005-12-13
You can synchronise with an online time server by running
```
sudo ntpdate pool.ntp.org
```.

Also check that you're set to the correct time zoneby running 
```
tzselect
```

---

### Post by jackyyong on 2007-03-14
This is no good. I have no internet connection at my machine with Xubuntu Edgy. I can't sync my time online, and XFCE's interface does not seem to allow me to change the date, unlike Ubuntu's Gnome interface. Any help please?

---

### Post by jackyyong on 2007-03-14
I accidentally bumped into something that I didn't notice before. Go to Applications -- System -- Time and Date!!

I can now manually edit the date and time, including the time zone, with GUI!

I selected "Keep clock synchronized with Internet Servers" and I was prompted to install ntp-simple and ntp-server. And it worked from then on! Brilliant! Guess I answered my own dumb question!

---

### Post by Dionysus135 on 2007-08-17
Is there anyway to adjust it using terminal?I have no internet connection on my xubuntu and when i go to applications--system--time and date it asks for adminstrator password and doesnt let me access the time and date.

---

### Post by ugm6hr on 2007-08-17
> **Dionysus135 said:**
> Is there anyway to adjust it using terminal?I have no internet connection on my xubuntu and when i go to applications--system--time and date it asks for adminstrator password and doesnt let me access the time and date.

You can generally change the time/date from the computer's BIOS.  Xubuntu should automatically pick that time up at reboot.

Bizarre it won't give you access to the time though....

---

