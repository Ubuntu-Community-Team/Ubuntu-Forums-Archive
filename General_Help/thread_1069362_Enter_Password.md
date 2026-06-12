---
title: "Enter Password"
date: 2009-02-13
forum: General Help
---

### Post by RedSingularity on 2009-02-13
I was just wondering, how come i am not asked to enter a password all the time?  Lets say i click the Update Manager.  I get a password prompt.  A few minutes later if i click it again i dont get the prompt.  Why is this?

---

### Post by MarblePanther on 2009-02-13
> **Shadow121 said:**
> I was just wondering, how come i am not asked to enter a password all the time?  Lets say i click the Update Manager.  I get a password prompt.  A few minutes later if i click it again i dont get the prompt.  Why is this?

It is a timeout setting.  This is for convenience purposes (I personally hate it and it is a security flaw imho)

If you want to change this: (it is advisable, but can be annoying typing the passwords over and over)
 
```
sudo visudo
```


and add 

```
,timestamp_timeout=0
```

to the end of the *defaults* line

For example:   
Defaults              env_reset,timestamp_timeout=0
is what it will look like

---

