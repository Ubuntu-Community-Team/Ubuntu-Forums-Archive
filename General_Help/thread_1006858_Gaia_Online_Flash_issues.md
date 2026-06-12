---
title: "Gaia Online Flash issues"
date: 2008-12-09
forum: General Help
---

### Post by Stephen Sasak on 2008-12-09
I don't know if this thread belongs here, but I am having issues with trying to play a game linked from a site on the internet.  It is called ZOMG on Gaia Online and apparently there is some issues about the flash plug-in for Ubuntu that does not allow it to run.  I use a IBM thinkpad with Ubuntu v8.10, and Mozilla Firefox is the web browser I use.

The game makes it to the point where I can choose what server I want to play on, but a message saying "104 Connection Time out"  and I don't know what to do to fix this.  Can someone help me out?

---

### Post by binbash on 2008-12-09
i am getting the same error with flash 10 firefox3.1b2 . Also aqworlds.com this game also does not work (same error you cant connect to servers)

---

### Post by Stephen Sasak on 2008-12-15
Can I assume no one has any idea how we can fix this?

---

### Post by maddog46113 on 2008-12-15
You may try using nspluginwrapper.

first you need to remove flash. I dont know what version you have installed. So after removing it. Go into terminal

```
 sudo apt-get install nspluginwrapper 
```
```
 sudo apt-get install flashplugin-nonfree
```
```
 sudo apt-get install flash-plugin-nonfree-extrasound
```

restart firefox and try it again.

---

### Post by maddog46113 on 2008-12-15
I just tried out Gaia Online. Mine works properly. Im using nspluginwrapper so give it a shot. It works here.

---

### Post by fm1234 on 2009-01-07
same issue here. nswrapper didn't help :(

any ideas of what could be wrong here: I also tried flash 9, which worked on version 8.04 with the same Firefox version. Alas, neither flash versions worked with Ubuntu 8.10. Could this be some networking issue with the kernel used in 8.10?

---

### Post by phantom3113 on 2009-02-16
I would have to agree that this didn't work. Could you elaborate on initially removing flash? I may not have done it correctly and that might be the issue.

---

