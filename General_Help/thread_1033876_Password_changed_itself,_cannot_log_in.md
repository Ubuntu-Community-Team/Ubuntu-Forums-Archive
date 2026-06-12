---
title: "Password changed itself, cannot log in"
date: 2009-01-07
forum: General Help
---

### Post by Rotarychainsaw on 2009-01-07
OK this sounds odd, but bare with me.

I don't change my password often, and I haven't changed it lately. I am trying to install hplip to get a new printer working and it wasn't accepting my sudo password. I rebooted and now I can't login. gdm seems to segfault when I put in my password. 

I booted into a recovery mode and tried to change my pass from the root prompt. I did 'passwd rotarychainsaw' (that segfaults) and 'usermod -ppass rotarychainsaw'. 

Neither work. Anyone know wtf is up?

---

### Post by sPiN1 on 2009-01-07
This might sound stupid but maybe you had caps lock on? Seems more likely than it changing itself. :P

---

### Post by Rotarychainsaw on 2009-01-07
Nope checked that haha. Also when to see if a key was not working or something, but all the dots come up.

---

### Post by Rotarychainsaw on 2009-01-07
Created a new user, putting in the right password segfaults the login on the CLI. THats odd... :-k

---

### Post by jerome1232 on 2009-01-07
Can you login to a tty? ctrl+alt+f1 then login. 

Could *possibly* be a full disk, ```
df -h
``` to check disk usage from a console.

---

### Post by Rotarychainsaw on 2009-01-07
can't login from a terminal... 

Im on a live cd now, the disk has 40gigs free. I was gonna copy my home folder onto my external, but the live cd wont let me. Some folders I dont have permissions...

---

### Post by Rotarychainsaw on 2009-01-07
Got the copying going. Probably just gonna reinstall and put my home folder back... Anyone know if there is a list of stuff I had installed so I don't have to find it again? Maybe in a apt-get config file somewhere?

---

