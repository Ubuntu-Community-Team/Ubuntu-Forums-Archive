---
title: "network issues, 2 ubuntu machines"
date: 2008-12-30
forum: General Help
---

### Post by deathsshadow77 on 2008-12-30
I recently put ubuntu 8.10 on my eee pc. Today I installed giver and synergy on both my desktop and my eee. Unfortunately they didnt detect each other. Im not really sure what the problem could be. Below is a map of how I have my network set up.

---

### Post by deathsshadow77 on 2008-12-31
bump

---

### Post by nothingspecial on 2008-12-31
What are you trying to do? Share files? Log in remotely? Listen to music or watch vids from your other machine?

---

### Post by cariboo on 2008-12-31
Can the computers ping each other?

Jim

---

### Post by deathsshadow77 on 2008-12-31
what im trying to do is use giver to send files and use synergy to use my desktop's mouse and keyboard on my eee pc.

Also how would I ping a computer on ubuntu?

---

### Post by Iowan on 2008-12-31
> **deathsshadow77 said:**
> Also how would I ping a computer on ubuntu? From a terminal, type **ping <target address>**  - substituting actual IP address for your target machine. It's also under System>Administration>Network Tools (on my Gutsy machine).

---

### Post by deathsshadow77 on 2008-12-31
ok, so i was able to ping both computers from each other

---

### Post by nothingspecial on 2009-01-01
I don`t know anything about this but google tells me you need avahi to let the computers see each other.

avahi is in the repos so

```
sudo apt-get install avahi
```

Hope that helps.

---

### Post by deathsshadow77 on 2009-01-01
tried it but no luck. it was actually already installed.

---

### Post by nothingspecial on 2009-01-01
Have you tried ssh and vinagre?

---

