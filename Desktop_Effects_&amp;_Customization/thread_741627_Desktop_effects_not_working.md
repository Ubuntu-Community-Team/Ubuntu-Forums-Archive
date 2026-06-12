---
title: "Desktop effects not working"
date: 2008-03-31
forum: Desktop Effects &amp; Customization
---

### Post by callkalpa on 2008-03-31
I'm using Ubuntu 7.10

When I try to activate the visual effects from the appearence preferences dialog, an error is occured saying "Desktop effects could not be enabled"

I have installed Compiz also and couldn't use it due to this issue.

How can I solve this ? Please help

Thanks you.

---

### Post by chewearn on 2008-03-31
There is no need to install compiz in Ubuntu Gutsy; it's already installed by default.
Please provide the specs of your graphics card.

---

### Post by callkalpa on 2008-03-31
Is there a particular command to get the specs of the graphics card ?

---

### Post by Helios1276 on 2008-04-01
I had trouble with my ATI card for quite a while , went through various series of commands and guides but in the end ended getting success using Envy, might work for ya ? good luck eitherway, I feel your pain!

---

### Post by chewearn on 2008-04-01
> **callkalpa said:**
> Is there a particular command to get the specs of the graphics card ?

Well, what brand or product number is mentioned on the packaging?  Duh! :lol:

If you really insist, run this command:
```
lspci | grep VGA
```

---

### Post by callkalpa on 2008-04-01
Below is the out put og lspci | grep VGA

01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

---

### Post by chewearn on 2008-04-01
> **callkalpa said:**
> Below is the out put og lspci | grep VGA

01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

Ah, I could be wrong, but VIA graphics is pretty old and probably don't have 3D acceleration.  That means, compiz not possible.

---

