---
title: "Can't run nautilus as root in console"
date: 2010-04-12
forum: Desktop Environments
---

### Post by chuchi on 2010-04-12
Hi friends!! How are you?? My problem is the follows: when I am in console, and I can't run nautilus as root. When I type "nautilus" in the console, I get a enormous error message. I post only the beginning:

```

(nautilus:4339): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported



```

---

### Post by 2hot6ft2 on 2010-04-12
Try
```
gksu nautilus
```

---

### Post by chuchi on 2010-04-13
Ok I'll try and tell you. Many thanks!

---

### Post by theozzlives on 2010-04-13
> **2hot6ft2 said:**
> Try
```
gksu nautilus
```

+1 for gksu!

---

### Post by theozzlives on 2010-04-13
> **chuchi said:**
> Hi friends!! How are you?? My problem is the follows: when I am in console, and I can't run nautilus as root. When I type "nautilus" in the console, I get a enormous error message. I post only the beginning:

```

(nautilus:4339): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported



```

Why you running a root console to begin with, nothing GUI will run from the console, boot GUI and do gksu from terminal.

---

### Post by chuchi on 2010-04-13
gksu nautilus works for me!! many thanks!! now i can navigate from the files as root

---

### Post by codemaniac on 2010-04-13
When you get your answers dont forget to mark the thread SOLVED..:KS

---

### Post by chuchi on 2010-04-14
OK I forgot it! but, how can I do it?? I don't how to mark a post as "Solved".

---

### Post by polki@mac.com on 2010-04-14
"Thread tools" way up there ^-^

---

### Post by chuchi on 2010-04-15
Thank you [email]polki@mac.com[/email], but if I click on "trhead tools", i only get a printable version. I still don't know how to mark a thread as "Solved".

---

