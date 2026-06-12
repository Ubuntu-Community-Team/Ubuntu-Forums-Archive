---
title: "How to open a html file from console?"
date: 2006-09-02
forum: Desktop Environments
---

### Post by linuxnewbie946 on 2006-09-02
How do I open a html file from the terminal?

---

### Post by taurus on 2006-09-02
If you don't have either lynx or links, then install it.  Then

```
lynx <filename>.html
```

---

### Post by daemonoid on 2006-09-02
or if you want to edit it:

vi <filename>.html

---

### Post by linuxnewbie946 on 2006-09-02
I want something generic..... like a command for everyone. I wish there could be a command like this:
 
 /path/to/file/search.html
 
 and it would open the file in the users default browser.

---

### Post by linuxnewbie946 on 2006-09-02
Is there anything like this?

---

### Post by njzillest on 2006-09-02
TRy 

mozilla <.html file> 

that should work.

---

### Post by az on 2006-09-02
> **taurus said:**
> If you don't have either lynx or links, then install it.  Then

```
lynx <filename>.html
```

w3m is installed by deafult and it replaces lynx.  I provides better localisation support than lynx.  Otherwise it is the same.

---

