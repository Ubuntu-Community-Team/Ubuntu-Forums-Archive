---
title: "ctrl-alt-del"
date: 2006-04-16
forum: Desktop Environments
---

### Post by WolfJay_83 on 2006-04-16
My laptop boots up to the text based login (no GDM or KDM, old machine). 

I just noticed that if, instead of loging in, I just press ctrl-alt-del it drops runlevels straight to the root prompt!  I can even create a file in / without ever entering a password.  Once I start x, this doesnt work, but whenever I'm at a text VT it works.

This seems like a major security vulnerability to me, but I'm not sure what the problem is, let alone how to fix it. Can someone point me in the right direction on this one?  Where are these low-level keybindings, or alternatively, how do I make it impossible to drop to this runlevel without root privleges?

Thanks a bunch!

---

### Post by jpkotta on 2006-04-16
I disabled CTRL-ALT-DEL on my VTs.  The setting is in /etc/inittab.  Just comment out the appropriate line:
```
# What to do when CTRL-ALT-DEL is pressed.
#ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now
```

---

### Post by WolfJay_83 on 2006-04-18
Thanks, that should do it... my this *is* an interesting file :-k

---

### Post by redr on 2008-01-03
Eevn I found the this problem, 
but I couldn't find the 'ininttab' file
I am using Ubuntu Feisty 7.04
Please help,
Thanks.

---

