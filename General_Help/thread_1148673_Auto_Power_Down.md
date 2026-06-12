---
title: "Auto Power Down?"
date: 2009-05-04
forum: General Help
---

### Post by CrusaderAD on 2009-05-04
Is it possible to schedule an auto-power down for the operating system? Say if I wanted to power down my machine everyday at 8:00pm?

---

### Post by motoaxe on 2009-05-04
You can set up a cron job to do that.

add this to your crontab file (crontab -e)

00 20 * * * /sbin/shutdown -h now

---

### Post by CrusaderAD on 2009-05-04
ok, I added that line. I take it "20" is the 8pm configuration? Thanks!

---

### Post by motoaxe on 2009-05-04
yeah, in order it goes: minute, hour (24 hr format), day, month, *day of the week*

---

### Post by binbash on 2009-05-04
install gshutdown if you want a gui ;)

---

### Post by CrusaderAD on 2009-05-05
Cool, thanks. The cron script works great, but I do like GUIs.

---

