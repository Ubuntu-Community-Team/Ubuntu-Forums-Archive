---
title: "HELP!  Can't update Kubuntu (Dapper).  Keeps asking for CD.  Don't have it!"
date: 2006-08-17
forum: Desktop Environments
---

### Post by theosib on 2006-08-17
I'm trying to use Adept Updater to bring my unstable Dapper system up to date.  Unfortunately, it keeps asking for my install CD, which I no longer have!  I could download and burn another one, but that may not be the one it wants.  How do I get it to just download whatever it needs from the internet instead?  (It's not being specific about what it wants from the CD.)

---

### Post by Infra on 2006-08-17
Check your /etc/apt/sources.list and remove the cd line from there. You should also put universe and multiverse repositories to that file.

---

