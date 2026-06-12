---
title: "Synaptic not working any more"
date: 2009-03-08
forum: General Help
---

### Post by sheshdd on 2009-03-08
Ok so i tried to install the plugins to listen to various media types on rythimbox,but not only the plugins weren't installed,but also Synaptic won't work anymore.So this is what the splash screen tells me when i start synaptic 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

so,i open the terminal and type "dpkg --configure -a",but it says that i need administrator privileges to do that.Thing is,i've been trying to figure out how to become the owner of the system,but i just can't,neither can i log in as root,on the logon screen it says that "root" can not login from there...soooo
what should i do?

---

### Post by Chemical Imbalance on 2009-03-08
put this before any command that requires root privileges:

```
sudo
```

this temporarily gives you administrative privileges from your normal user account.

So basically you want this:
```
sudo dpkg --configure -a
```

---

### Post by sheshdd on 2009-03-09
yay it worked!thanks man!

---

### Post by Chemical Imbalance on 2009-03-09
No problem!

:D

---

