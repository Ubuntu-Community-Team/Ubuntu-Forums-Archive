---
title: "question"
date: 2009-06-02
forum: General Help
---

### Post by luis_oki on 2009-06-02
hi, I need your help for this question please:
 
which file contains a list of currently mounted file systems?
 
thanks

---

### Post by VMC on 2009-06-02
> **luis_oki said:**
> hi, I need your help for this question please:
 
which file contains a list of currently mounted file systems?
 
thanks

command **mount** will tell you what you have mounted, if that's what your asking.

---

### Post by luis_oki on 2009-06-02
yes , thanks...

---

### Post by jonobr on 2009-06-02
Stupid question  Did you mean the file name is editorial?

If so, the easiest way is using a text editor like vi
vi can be quirky to people not used to it.
Make a backup of your file

cp editorial editorial.bkup

type vi editorial

When you get in there be careful!!

You can quit by hitting escape and then q!

To search and replace in the file type 

:%s/lady/Lady/g

When the names are replaced, hit escape again, and then wq! (writes to and quits the file)

the %s indicates a search, lady is the argument to search for 
Lady is the replacement and g searches for all occurances in the file

Also what do you mean by
spedify a user´s home directory?

---

### Post by VMC on 2009-06-02
**cd** to the folder you want to change and do the following(the '-n' is just a test. When sure remove it):

```
rename -n 's/^lady/Lady/' *
```

---

### Post by luis_oki on 2009-06-02
ah ok... and what is the command used to view jobs scheduled to run at regular intervals?

---

### Post by luis_oki on 2009-06-02
??

---

### Post by luis_oki on 2009-06-02
what is the command used to view jobs scheduled to run at regular intervals?
please help

---

### Post by Iowan on 2009-06-02
Check via **less /etc/crontab**.  Is that the one you mean?

---

### Post by luis_oki on 2009-06-03
yes, thank you ;)

---

