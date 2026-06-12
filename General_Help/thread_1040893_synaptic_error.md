---
title: "synaptic error"
date: 2009-01-16
forum: General Help
---

### Post by witebred on 2009-01-16
everytime i go to use synaptic i get an error and says 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can someone help me figure this out

IM me [email]dtarry112@live.com[/email] if you can help thnx

---

### Post by howefield on 2009-01-16
Open a terminal, applications > accessories > terminal and type
```

sudo dpkg --configure -a
```

Enter your password when asked.

---

### Post by iaculallad on 2009-01-16
> **howefield said:**
> Enter your password when asked.

And, you don't have to worry if you don't see the characters being echoed back on your screen. That's just normal for security purposes. Just type the privileged password and hit on your Enter key.

---

### Post by witebred on 2009-01-16
thank you good sirs:guitar:

---

