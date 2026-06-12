---
title: "root password for foomatic-gui"
date: 2005-03-16
forum: Desktop Environments
---

### Post by jamaas on 2005-03-16
I've installed foomatic-gui for gnome and when I try and run it, it asks me for a root password. I give it the one for su, but it doesn't seem to be happy with that.  Is there a way I can assign a root password or get around this problem and run foomatic-gui?

thanks

Jim

---

### Post by lorap on 2005-03-16
i'd the same prompt after XCDROASTER's installation.
but only at first running cause it asked me to set setting and as you know you'd be a root.have you typed in your right root password?
pavel

p.s.:
grant this application more rights this way:

sudo chmod 222 /the path to the app/app

so everyone can run it.let me know if it worked.

---

### Post by jamaas on 2005-03-16
Is the root password different from that of su?

I know I typed the su password in correctly, tried it carefully several times.

thanks

Jim

---

### Post by lorap on 2005-03-16
grant this application more rights this way:

sudo chmod 222 /the path to the app/app


pavel

---

### Post by dusu on 2005-03-16
I don't know if this will solve your problem...
What I did, very soon after the install was to change the root passwd by doing :
```
sudo passwd root
``` 
You can then enter the password for root, login as root, and do anything as root...

Maybe you can give it a try.

---

### Post by jamaas on 2005-03-16
Thanks Dusu,

That did fix that problem.... now I get no error message after putting in the password ... but nothing happens at all and it appears that the foomatic-gui program does not execute ?

Any thoughts?

Thanks

Jim

---

### Post by dusu on 2005-03-16
I do not know foomatic-gui, so I can't help you any more, but I hope someone else can help you with this new problem...

---

### Post by lorap on 2005-03-16
try to run it in terminal,so you'd be able to see what it writes.
pavel

---

