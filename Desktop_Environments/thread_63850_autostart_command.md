---
title: "autostart command"
date: 2005-09-09
forum: Desktop Environments
---

### Post by ultima2k on 2005-09-09
I use the app hotkeys to be able to use my special keyboard buttons in ubuntu. It doesn't autostart with ubuntu so I always have to use the command "hotkeys -t itouch" to start it..

How can I make it automaticly start??

---

### Post by akcanadianeh on 2005-09-09
Log in to Ubuntu, open terminal, type
```
hotkeys -t itouch
```
(you knew that part)
Log out, **checking the Save Settings ** box on your way past the log-out menu.
Log back in, and it should start automatically!
Yay!    :grin:   (Hope it works for ya)

---

### Post by ultima2k on 2005-09-12
Didn't work :(

---

### Post by ultima2k on 2005-09-17
now how do I do?

---

### Post by Corvillus on 2005-09-17
Under the System -> Preferences menu, click Sessions, then the Startup programs tab, then add the command you want to be run on startup (hotkeys -t itouch)

---

