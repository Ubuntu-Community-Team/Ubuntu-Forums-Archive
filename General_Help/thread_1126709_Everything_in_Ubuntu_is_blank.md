---
title: "Everything in Ubuntu is blank"
date: 2009-04-15
forum: General Help
---

### Post by bnciwebdesign on 2009-04-15
I was watchin a movie and suddenly everything froze up, so I restarted my computer and tried to finish the movie and all my windows just started up blank, no words, even terminal wont work...what happened and how do I fix this?

---

### Post by codeseer on 2009-04-15
Try pressing CTRL + ALT + Backspace.

---

### Post by rage9 on 2009-04-15
Log out then in.

---

### Post by bnciwebdesign on 2009-04-16
> **codeseer said:**
> Try pressing CTRL + ALT + Backspace.

I got an error,

Could not start the X
server (your grahpical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be 
disabled. Please restart GDM when 
the problem is corrected

---

### Post by Daisuke_Aramaki on 2009-04-16
> **bnciwebdesign said:**
> I got an error,

Could not start the X
server (your grahpical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be 
disabled. Please restart GDM when 
the problem is corrected

Of course you just got out of X.

Do this

```
sudo /etc/init.d/gdm stop
```

Then
```
sudo /etc/init.d/gdm start
```

you will be taken back to the login screen. I am assuming you use gdm

---

### Post by bnciwebdesign on 2009-04-16
Thanks, Idk if it was the inode errors that kept asking to be corrected or the last thing said, but it worked!!!

---

### Post by bnciwebdesign on 2009-04-23
I got the blank thing again, and when I stopped and restarted the GDM, it gave me the same error...?


Any Ideas?

---

