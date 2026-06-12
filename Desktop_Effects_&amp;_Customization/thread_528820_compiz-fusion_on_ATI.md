---
title: "compiz-fusion on ATI"
date: 2007-08-18
forum: Desktop Effects &amp; Customization
---

### Post by idanool on 2007-08-18
using ubuntu 7.04
I had compiz fusion 0.5.2 working, 
then I installed the ATI restricted driver,
and now compiz won't run.

>compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by Motoxrdude on 2007-08-18
The fglrx drivers (restricted ati drivers) do no support aiglx, so you have to create an xgl session. Here is a howto, hope this helps.
[http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+ati+howto](http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+ati+howto)

---

### Post by idanool on 2007-08-18
thanks for your fast reply!
it works !

---

### Post by Motoxrdude on 2007-08-19
awesome! i am glad to hear it.

---

