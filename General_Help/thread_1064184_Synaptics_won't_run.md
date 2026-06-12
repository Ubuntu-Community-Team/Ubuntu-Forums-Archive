---
title: "Synaptics won't run"
date: 2009-02-08
forum: General Help
---

### Post by James49 on 2009-02-08
Hi
 Sorry if this seems a simple question, but I'm new to Linux. I'm using Ubuntu 8.04. 
Synaptics was working perfectly when first installed, but now if I try to run it I get the following error message:-
'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.'

I have tried to run dpkg as shown in the terminal window (which I assume is correct) but I keep getting the message that I need 'superuser privilege' to do so. I have no idea what this is, or how to go about it and the help system doesn't seem to have heard of 'superuser privilege,' never mind how to use it!

Any advice would be warmly welcomed.

James

---

### Post by howefield on 2009-02-08
Precede the command with sudo eg,

```
sudo dpkg --configure -a
```

Type your password when it asks for it and then press enter.

---

### Post by Nepherte on 2009-02-08
Run
```
sudo dpkg --configure -a
```

---

### Post by James49 on 2009-02-08
Thank you both - problem solved.

Cheers, James

---

