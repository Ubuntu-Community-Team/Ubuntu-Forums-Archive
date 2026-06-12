---
title: "Logging in twice to log in?"
date: 2008-06-26
forum: Desktop Environments
---

### Post by ChromeKaldra on 2008-06-26
Hey, i'm plagued by an annoying little occurence. When i go to log into my user account, after i punch in the name and password [correctly] the screen flashes to a screen of code then refreshes back at the log-in page, where i have to punch in my name and password again. It goes through the second time fine, and i get into my account, but i'm still a little worried.

---

### Post by krodiak on 2008-06-26
It seems its a screen resolution problem, same thing happened to me... thats beacuse the resolution using during boot it's different to the resolution of gdm.

Install startupmanager

```


sudo apt-get install startupmanager

```
Then in the Screen selection use the resolution u normally use in gdm, reboot and should do the trick

---

