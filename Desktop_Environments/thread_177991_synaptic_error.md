---
title: "synaptic error"
date: 2006-05-17
forum: Desktop Environments
---

### Post by markitos on 2006-05-17
I have recently installed kde on my Ubuntu and now I am having errors when using Synaptic. The error says:
"E: samba: subprocess post-installation script returned error exit status 102"
My Ubuntu is finnish and for some reason the Kde desktop that I installed is now english. I have tried to istall language packs but everytime I get that error. I hope someone can help me.

---

### Post by louis_nichols on 2006-05-17
Well... if samba is not required by kde, which I don't know for sure, you can just remove it: sudo apt-get remove samba

Then you should be back on track, installing any package you like.

---

### Post by markitos on 2006-05-17
I tried to remove samba but with same errors: 
"Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Any ideas?
By the way, should I use synaptic or Adept or does it matter?

Thanks

---

### Post by louis_nichols on 2006-05-17
don't think it matters. strange what's happening. try (re)configuring it

sudo dpkg --configure samba

I think that's the command

---

### Post by markitos on 2006-05-17
:( 
"dpkg: error processing samba (--configure):
 package samba is already installed and configured
Errors were encountered while processing:
 samba"

This came out after trying to configure Samba.... I hope someone can help me.

---

### Post by louis_nichols on 2006-05-18
sorry, I must have missed your last post on the thread when looking through my subscribed threads.

I'm sorry that I can't replicate your problem, to give you a certain answer. so I can only guess possible solutions. I would try this command next, when all else has failed:

sudo dpkg-reconfigure samba

---

### Post by maser on 2006-05-18
I had the same problem. Removing that symlink in /etc/rc2.d/ solved it.

---

### Post by markitos on 2006-05-18
I did the same thing, erased that file, after that everything seems to work normal. No more errors when using packet programs. Sure I dont know whats the purpose of that file but perhaps someone could explain what are those rc-folders.

---

