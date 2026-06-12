---
title: "Disabling Capslock"
date: 2009-05-17
forum: Desktop Environments
---

### Post by skewray on 2009-05-17
What is the preferred method for KDE users to disable the caps-lock key?

Thanks, Brian

---

### Post by skewray on 2010-09-08
bump

---

### Post by ankspo71 on 2010-09-08
Hi,
KDE 4.5 has the option to do this at: 
System Settings > Input Devices > Keyboard > Advanced (tab)
then enable "Configure Keyboard Options"
Next move down to "CapsLock Key Behavior"
Then check the box that says "CapsLock is Disabled"

KDE 4.4 should be similar.

Hope this helps.

---

### Post by ankspo71 on 2010-09-08
Hi,
I found another thread covering this at:
[http://kubuntuforums.net/forums/index.php?topic=3104753.0](http://kubuntuforums.net/forums/index.php?topic=3104753.0)
One poster mentions how to use xmodmap at startup to disable capslock.
Another user recommended using the GUI way by going to 
SystemSettings>Regional&Language>KeyboardLayout>Advanced
(this should be the KDE 4.4x settings)

---

### Post by skewray on 2010-09-11
> **ankspo71 said:**
> Hi,
KDE 4.5 has the option to do this at: 
System Settings > Input Devices > Keyboard > Advanced (tab)
then enable "Configure Keyboard Options"
Next move down to "CapsLock Key Behavior"
Then check the box that says "CapsLock is Disabled"

KDE 4.4 should be similar.

Hope this helps.

I am not sure which version I am using (whatever comes on lucid), but I don't have a System Settings > Input Devices.
I do have System Settings > Regional & Language > Keyboard Layout > Advanced, but everything is grayed out and can't be changed.  Sigh.  I guess I will use .xmodmap.  Thanks!

---

