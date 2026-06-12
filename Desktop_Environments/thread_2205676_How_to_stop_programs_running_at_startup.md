---
title: "How to stop programs running at startup?"
date: 2014-02-15
forum: Desktop Environments
---

### Post by gicanzo on 2014-02-15
Hi everyone,
I have recently installed Xubuntu 13.10 on my Toshiba Satellite. There is one little problem that I wasn't able to solve.
I have Google Chrome and LibreOffice running automatically at startup. I think this happened after I set Thunderbird for automatic startup through the settings manager.
If I access the setting manager, Chrome and libreoffice are not in the list of programs running at startup. How can I prevent them to run automatically?
This is not a big issue, but a bit annoying. I am a half noob with regards to Linux so please try to be clear with explanations :D

Edit: forgot to mention that I looked at the internal settings for both chrome and libreoffice, but I could not find any option such as "run at startup".

---

### Post by Frogs Hair on 2014-02-15
Try navigating to session and start-up and clearing saved sessions.

---

### Post by buzzingrobot on 2014-02-15
I don't have XFCE available, but I know it has a configurable "Sessions" setting that, optionally, will restart apps previously running on the next reboot or new login.

---

### Post by gicanzo on 2014-02-15
> **Frogs Hair said:**
> Try navigating to session and start-up and clearing saved sessions.

Ehmm.. could you be more precise? As I said, I'm kinda noob with Linux and especially with Xubuntu, which I installed 2 days ago for the first time.

---

### Post by zealibib slaughter on 2014-02-15
Open settings manager in your main menu, under system you will find session and startup, in Session and startup navigate to the session tab and clear saved sessions with the button at the bottom, navigate to application autostart and disable anything you dont want to start up automatically.

Sometimes when you shutdown improperly or shutdown when you have open applications they will autostart due to saved sessions so you may need to do this every so often when that happens.

---

### Post by Frogs Hair on 2014-02-15
> **gicanzo said:**
> Ehmm.. could you be more precise? As I said, I'm kinda noob with Linux and especially with Xubuntu, which I installed 2 days ago for the first time.

Excuse me , see the post above . I didn't explain further because session and  start-up is a menu item.

---

### Post by tgalati4 on 2014-02-15
Some applications have a preference for "Start up at Boot".  XFCE has a session manager that tries to reload everything you had open when you last shut down.  This is in the control panel.  So you would need to clear both to prevent an application from opening automatically.

---

### Post by gicanzo on 2014-02-16
I cleared saved sessions and it worked. Thanks!

---

