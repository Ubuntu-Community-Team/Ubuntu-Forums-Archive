---
title: "Screen Resolution pref error"
date: 2005-04-02
forum: Desktop Environments
---

### Post by vaskark on 2005-04-02
I get this error when I run the Screen Resolution preference app:

> The X Server does not support the XRandR extension. Runtime resolution changes to the display size are not available.
Any ideas?

---

### Post by kurros on 2005-04-02
It sounds like the driver you are using doesnt support XRandR. The ATI FGLRX drivers do not support it, for example.

---

### Post by vaskark on 2005-04-02
[QUOTE=kurros]It sounds like the driver you are using doesnt support XRandR. The ATI FGLRX drivers do not support it, for example.[/QUOTE]
Yeah, I am using the fglrx driver. Dang.

---

### Post by askreet on 2005-04-02
Easy enough fix, just edit the config file and restard X, little more work involved but no big deal. With GDM running it'll reopen for you automatically :D

---

### Post by Battery on 2005-07-11
[QUOTE=askreet]Easy enough fix, just edit the config file and restard X, little more work involved but no big deal. With GDM running it'll reopen for you automatically :D[/QUOTE]


how?

---

