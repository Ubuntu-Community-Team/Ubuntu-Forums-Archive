---
title: "Changing individual folders from root privileges"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Donald F. Robertson on 2006-07-24
I can't figure out how to modify a folder with "root" privileges with the default desktop, and I can't seem to manage it in the command line.  This has stumped me several times, most critically when I was attempting to back up a day's Moneydance work to CD.  For some reason the CD suddenly decided it had root privileges and I could not write to it.  Nor could I modify its privileges.  Eventually, I gave up and used another CD, but obviously you can't do that with every folder.

For the most part, I've found this lack of superuser / root login more of a pain in the neck than a simplification.  Subo is intermittently useful, but is mostly confusing for this relatively novice user.

-- Donald

---

### Post by philippe_carlo on 2006-07-24
I would think the exact oposite. The advantage of sudo is that some crucial environment variables are preserved, allowing the use of the X display, giving you just enough power to do what you want, and very configurable too!

Loging in as root is still possible, just type 'sudo bash' at the prompt.

---

### Post by Thund3rstruck on 2006-07-24
Even with modern corporate windows implementations the "root" or local administrator account is never accessable to the ordinary user. In fact all administrators in my organization are required to utilize 'runas' (the windows equivelenet of sudo) in order to perform tasks as local or domain administrators. 

Perhaps from a home user perspective this is awkward but not to an enterprise user.

---

### Post by tturrisi on 2006-07-24
> **Donald F. Robertson said:**
> I can't figure out how to modify a folder with "root" privileges with the default desktop, and I can't seem to manage it in the command line.  This has stumped me several times, most critically when I was attempting to back up a day's Moneydance work to CD.  For some reason the CD suddenly decided it had root privileges and I could not write to it.  Nor could I modify its privileges.  Eventually, I gave up and used another CD, but obviously you can't do that with every folder.

-- Donald
an easy graphical method:
1. Applications > System Tools > Run as different user
2. Run: Nautilus    User: root
3. rt click any dir & set permissions, ownerships, etc.

just be careful which dirs you alter as could possibly cause errors in later in other applications.

---

### Post by Donald F. Robertson on 2006-08-03
Thank you very much.

-- Donald

---

