---
title: "XScreenSaver 5.08 - How to either Disable or Unistall?"
date: 2010-07-29
forum: Desktop Environments
---

### Post by Sky Aisling on 2010-07-29
Hello,

I am helping a friend with her new Karmic Koala system on her new ZaReason 3660 Strata. I added XScreenSaver 5.08 to her applications list.  We've had issues with XScreenSaver and want to either disable or uninstall the application.  We cannot figure out how to disable XScreensaver and revert to the original screensaver app that came with the system.  When I use Snaptics Package Manager to either 'completely' uninstall', or just 'uninstall' the message says that I will uninstall the 'desktop'.

Does this mean I will uninstall only the desktop version of XScreenSaver applilcation?  *Or*, does this mean I will uninstall the system desktop (in this case Xfce)?  I'm a little hesitant to punch the button in case I blow off Xfce desktop!

Our goal is to either disable or uninstall XScreenSaver 5.08.  Then be able to use the screensaver that came with the system.

Thank you for your time and attention to my question.

Sky

---

### Post by TheStroj on 2010-07-29
If you installed from source, files will be in /usr/local directory and from there you can delete them (i'm not sure if that's a good thing to do, but the application will no longer be in use).

---

### Post by Sky Aisling on 2010-12-12
We're installing MeerKat.  We'll see where that goes with the screensaver.  :)

---

### Post by paulocoghi on 2011-02-03
Just type in terminal:

```
sudo apt-get remove xscreensaver
```

Thus it will remove the package "xscreensaver" and not remove other packages like "ubuntu-desktop".

And yes, the latter refers to the ubuntu system.

---

### Post by Sky Aisling on 2011-02-03
Thank you, [paulocoghi]("http://ubuntuforums.org/member.php?u=1029906")

---

### Post by ozone702 on 2011-03-29
> **paulocoghi said:**
> Just type in terminal:

```
sudo apt-get remove xscreensaver
```

Thus it will remove the package "xscreensaver" and not remove other packages like "ubuntu-desktop".

And yes, the latter refers to the ubuntu system.

Yea, thanks Paul!  Worked perfectly :)

---

