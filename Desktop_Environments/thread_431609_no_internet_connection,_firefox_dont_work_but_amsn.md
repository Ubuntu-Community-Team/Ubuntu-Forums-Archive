---
title: "no internet connection, firefox dont work but amsn does...really weird"
date: 2007-05-03
forum: Desktop Environments
---

### Post by fouadk on 2007-05-03
hey all

i have done a clean install to 7.04....my computer is part of a home network....my computer dual boot with xp....my computer is connected to a win xp computer and does connect to the internet via ICS(internet connection sharing from the part of the XP box)...it does connect normally when i boot xp but does not connect with i boot ubuntu,,,,this problem never existed with 5.10 ,6.06 ,6.10 and the weird thing is that amsn connect to the internet but firefox does not...that was two days ago...now nothing connects to the internet even though i can ping both machines.... 

please help...

thanks in advance

---

### Post by mojoman on 2007-05-06
Can you ping an external server?

try pinging google.
```

ping -c 3 72.14.203.99
```

and
```

ping -c 3 www.google.com
```

If the first works but the second does not this suggest you have a problem with your dns. In that case you need to edit the file /etc/resolv.conf, which should contain the dns that your ISP gave you.

/mojoman

---

