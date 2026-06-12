---
title: "desktop"
date: 2010-11-04
forum: Desktop Environments
---

### Post by davidca47 on 2010-11-04
Hi there!!
This is my first thread here and after installing Linux ubuntu on the desktop, when I minimize firefox, or any other application that I have opened they go the the right bottom side of  monitor and disapear there. I have no access to them anymore. i can't see them to reopen them. and clicking on firefox opens a new window. This eventually crash the computer too many application open.
Please help me with this.

---

### Post by 3Miro on 2010-11-04
Reasons for this could be:

1. You removed the Windows List form the bottom panel. Right click on it and add a Windows List applet.

2. There may be something wrong with your monitor settings. How many monitors are you using? Go to System -> Prefs -> Monitor to check what your settings are.

3. Something may be very wrong with the windows manager. Can you access the minimized applications via Alt + Tab.

---

### Post by davidca47 on 2010-11-04
Thank you very much 3Miro!
It was number 1 and 3. I added it now. How about rubish bin I can only add it to the panel not the desktop.
David

---

### Post by wojox on 2010-11-04
> **davidca47 said:**
> Thank you very much 3Miro!
It was number 1 and 3. I added it now. How about rubish bin I can only add it to the panel not the desktop.
David

Try Alt+F2

Enter gconf-editor

Go to apps > nautilus > desktop and check the box.

---

### Post by thameera on 2010-11-04
> **davidca47 said:**
> Thank you very much 3Miro!
It was number 1 and 3. I added it now. How about rubish bin I can only add it to the panel not the desktop.
David

If you're a newbie to Ubuntu, try an app like Ubuntu Tweak. It allows you to do basic tasks like these without any prior knowledge.

---

