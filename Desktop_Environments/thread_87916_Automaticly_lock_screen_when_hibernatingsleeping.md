---
title: "Automaticly lock screen when hibernating/sleeping"
date: 2005-11-09
forum: Desktop Environments
---

### Post by ola on 2005-11-09
Does anyone know how to lock the screen when hibernating the computer? I currently use the kscreensaver package (if that may be a problem).

---

### Post by Kyral on 2005-11-09
I don't use KDE....but you should be able to set the screensaver to lock the screen BEFORE it Hibernates. (Like where you set how long before it hibernates)

---

### Post by wrtrdood on 2005-11-09
This is one I need too.  The klaptop app works flawlessly except that I don't have it locking my screen before it hibernates or suspends.  Sort of frustrating.  I think what ola means is that it would be nice to just close the lid and walk off, knowing the X display will be locked when you come back to it.  I had this working under Ubuntu using the sleepd daemon.  That should still probably work well but it was not nearly as responsive as the latest klaptop daemon.  It also had the annoying habit of not recognizing when I was back on A.C. and would sleep the computer while I was typing on my external keyboard.

Though I've not had time to configure and check it, I think the solution would probably be an entry in the klaptop configuration for the application to run before hibernation and place the appropriate screensaver command there.

---

