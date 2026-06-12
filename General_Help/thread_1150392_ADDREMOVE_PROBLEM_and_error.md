---
title: "ADD/REMOVE PROBLEM and error"
date: 2009-05-06
forum: General Help
---

### Post by mjs1512 on 2009-05-06
When using add remove I get the message. 


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thanks

Just upgraded to 9.04, stand alone no windows or dual boot.

  intell core duo

---

### Post by Zoowey on 2009-05-06
> **mjs1512 said:**
> When using add remove I get the message. 


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thanks

Just upgraded to 9.04, stand alone no windows or dual boot.

  intell core duo

Well try running the command it tells you in a terminal.

sudo dpkg --configure -a

---

### Post by mjs1512 on 2009-05-06
Thanks for the reply. 
I just finished reading the forum  about running commands with out knowing what they do (Absolute Newbie) so I as I don't know what it does? I did not run it.

Cheers.

---

### Post by Zoowey on 2009-05-06
> **mjs1512 said:**
> Thanks for the reply. 
I just finished reading the forum  about running commands with out knowing what they do (Absolute Newbie) so I as I don't know what it does? I did not run it.

Cheers.

You shouldn't run random commands you find off of Google. But Ubuntu itself told you to run the command so it shouldn't break anything.

---

### Post by akoskm on 2009-05-06
> **mjs1512 said:**
> Thanks for the reply. 
I just finished reading the forum  about running commands with out knowing what they do (Absolute Newbie) so I as I don't know what it does? I did not run it.

Cheers.

Anyway if you don't believe to the gurus check what does it actually make:
```

man dpkg

```
it'll open for you the manual entry for the program dpkg.

---

### Post by mjs1512 on 2009-05-06
I ran the lines in terminal
it gave me another error  
I rebooted and update manager wanted to install updates
updates in stalled and problem gone.

Thank you for the replies.

---

