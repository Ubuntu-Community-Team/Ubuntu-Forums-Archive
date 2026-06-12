---
title: "is there any way i can make a user that doesnt have access to anything except firefox"
date: 2009-05-26
forum: General Help
---

### Post by phoenixjgibson on 2009-05-26
i kinda run IT for my work at a hotel, and i am running ubuntu on the guest comp. i have a serious problem with people screwing around with the settings! i have stripped the pannels and people still find ways to mess with the system...so is there any way to kill all access to the system except for running firefox for one user/ set a password for doing anything to the system?

---

### Post by phoenixjgibson on 2009-05-26
bump

---

### Post by pbpersson on 2009-05-26
I am assuming they only mess with their settings, right?

Create a test user, then change some settings - then scan that home directory for last modified date, find where the directories are, remove write access from those directories for that user.

Repeat this until you have it sufficiently locked down but not so locked down that they can't use it.

If you only want them to run Mozilla one would think they would only need access to the hidden directory .mozilla but perhaps that answer is too easy.

---

### Post by nothingspecial on 2009-05-27
You could remove the panels all together and disable all keyboard shortcuts except for one really complicated one to launch firefox.

---

### Post by glotz on 2009-05-27
Perhaps install this instead [http://en.wikipedia.org/wiki/Webconverger](http://en.wikipedia.org/wiki/Webconverger)

Or then allow them to do it all and have the cleaning staff restore an [image](http://www.partimage.org/) of a clean install as a part of the routine. ;)

---

### Post by mixmaster on 2009-05-27
Run it off a read-only filesystem?

---

### Post by pastalavista on 2009-05-27
As soon as you originally logon, switch to the "guest session" (new feature in 8.10 & 9.04).. they can use any app they want but can't permanently change any system settings at all. If they do muck up the session, just log out and back in (to the guest session) and it's back the way it started. No guests ever need a password either.

---

### Post by phoenixjgibson on 2009-05-30
thanks for all the help guys! the guest session is working so far, if that doesnt work in the long run then i will mess with the file permissions ;?)

---

