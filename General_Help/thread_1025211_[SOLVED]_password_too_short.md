---
title: "[SOLVED] password too short"
date: 2008-12-29
forum: General Help
---

### Post by meself on 2008-12-29
Hi.  I am trying to create a guest user account with the five character password of "guest".  This in not a security machine.  Guest usage is forcast to be very intermittent so I wanted a password that is self explainatory.

Unfortunately, Ubuntu tells me that this password is too short and at least 6 characters are required.  Is there a work around for that?

---

### Post by tuxxy on 2008-12-29
Couldnt you use something like "guests" would be quicker

---

### Post by oilchangeguy on 2008-12-29
> **meself said:**
> Hi.  I am trying to create a guest user account with the five character password of "guest".  This in not a security machine.  Guest usage is forcast to be very intermittent so I wanted a password that is self explainatory.

Unfortunately, Ubuntu tells me that this password is too short and at least 6 characters are required.  Is there a work around for that?

use ubuntu as the password.

---

### Post by eBoxNet on 2008-12-29
try to create your user with password guests and then do :

```
sudo passwd guest
```
enter your new short password. i.e. guest

---

### Post by meself on 2008-12-29
Thank you bBoxNet.  That worked fine.

---

### Post by eBoxNet on 2008-12-29
you are welcome,mark this as solved !

---

### Post by meself on 2008-12-29
how does one "mark this as solved"?  i cannot find a button to "mark this as solved".

---

### Post by Nathan Sweeney on 2008-12-29
> **meself said:**
> how does one "mark this as solved"?  i cannot find a button to "mark this as solved".
Thread tools at the top, "Mark this thread as solved"

---

