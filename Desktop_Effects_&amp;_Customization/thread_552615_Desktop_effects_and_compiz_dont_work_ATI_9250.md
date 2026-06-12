---
title: "Desktop effects and compiz dont work? ATI 9250"
date: 2007-09-16
forum: Desktop Effects &amp; Customization
---

### Post by sccrstvn93 on 2007-09-16
While trying to get the correct resolution for my screen i somehow made Desktop effects stop working. They worked before but now it says they cannot be enabled. I think i must have installed a new driver. Envy does not install a new drver for me. Also when i follow these instructions to get compiz: [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385) I cannot het to the desktiop with XGL Is there a way to make XGL work with my graphics card. Should i use AXGL instead? What drivers do i need? I have an ATI 9250.

---

### Post by kellemes on 2007-09-16
You tried to follow the thread?
What's not going right? Please give a little more info about your issue..

---

### Post by sccrstvn93 on 2007-09-16
It says: "Now test your login. Logout, click sessions and chose GNOME with XGL. If you get to the desktop you're now very close." It doesnt work. The screen reamins the yellowish orange color for 5 seconds and then goes back to the login.

---

### Post by Salazar420 on 2007-09-16
Maybe it's something as simple as "direct-rendering." Is yours still enabled? I am running the very same card, and have had issues with compiz and direct rendering in the past. Alas, I forget how to check for direct rendering, so you will have to find that info elsewhere (should be easy). Sorry for my ignorance.

---

### Post by sccrstvn93 on 2007-09-16
Thx for your help ill try that. But you are able to get compiz to run? Thats good news to me.

---

### Post by sccrstvn93 on 2007-09-16
im not finding how to disable direct rendering anywhere can someone point me in the right direction?

Edit: how do i check if it is enabled. and how do i check what driver i am using?

Edit: grep -i "Direct rendering" /var/log/Xorg.0.log that says direct rendering is disabled.

---

### Post by Arsic on 2007-09-20
Some bump. I have the same card and the same problem. Direct rendering turned on should fix it? (can see it by *glxinfo | grep direct*, btw)

How do I turn it on?

---

