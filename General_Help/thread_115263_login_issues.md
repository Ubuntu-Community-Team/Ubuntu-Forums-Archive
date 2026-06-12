---
title: "login issues"
date: 2006-01-10
forum: General Help
---

### Post by RikkiD04 on 2006-01-10
when i start up ubuntu under any session except failsafe terminal, i get this message:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

view details (~/.xsession-errors file)"

i have more diskspace and i i've already tried reinstalling my xserver. i still have the same message, and i'm not able to log on

please help me!

---

### Post by Susana on 2006-01-10
Hello,
log in to the failsafe terminal and check the ownership of .ICEauthority in your home directory. If it is root:root change it to user:user: sudo chown user:user .ICEauthority

---

