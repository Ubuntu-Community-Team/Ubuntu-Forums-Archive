---
title: "&quot;Key Ring Not Unlocked&quot; Prompt Is Now Gone"
date: 2015-04-22
forum: Desktop Environments
---

### Post by jrr2 on 2015-04-22
When I installed Xubuntu 14.04, I set it to login automatically. So, the keyring does not get unlocked during login. Normally, when at a website that needs user/pass information, I get the "your keyring did not get unlocked" prompt which asks for a password, and then it works fine.


However, in the last week or so, this keyring prompt is gone -- it never appears and so the keyring is locked. The only thing I figured out to do was log out and then enter my password on login screen and then log back in. This is very annoying since I have to log on twice now.


Does anyone know what could cause this? There have been a lot of updates lately. Anyone else having same problem?

---

### Post by dino99 on 2015-04-23
Looks like you need to report that bug (not sure about the xubuntu package name, report against one of the  libpam-xxxx installed)

---

### Post by jrr2 on 2015-04-25
> **dino99 said:**
> Looks like you need to report that bug (not sure about the xubuntu package name, report against one of the  libpam-xxxx installed)

Thanks for the response. 


How do you go about reporting a bug? I've never done that. Also, I am not technically adept with this, so I have no idea what libpam  is.

---

### Post by cetoka on 2015-05-07
I had the same problem.I am using Ubuntu 14.04 LTS. It started last week,but I was able to solve it. I deleted the .config  google-chrome, and chrome started as it was freshly installed.I would advise you to backup your bookmarks and passwords because after deleting .config  google-chrome you have nothing left.After setting up chrome changing settings and adding passwords chrome started to ask for the keyring again.I hope this helps.

---

