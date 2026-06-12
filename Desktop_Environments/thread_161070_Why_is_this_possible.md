---
title: "Why is this possible ?"
date: 2006-04-16
forum: Desktop Environments
---

### Post by index_0@ya.com on 2006-04-16
Hi thr,, 
      I (perhaps u might have too !)  noted an intresting behaviour in Ubuntu shell ,
 If go to another , terminal ( i mean ctrl+alt+f1) and login as non-root , and type reboot , and system is smart enough to say , 
Permission is denied ,only root can do tht

oh ya ,, wht if u giv an ctrl+alt+del or hit the power button? 
The system reboots instantly , force kill evry running app, 

but, this functionality is well trapped in recovery mode ! :cool: 

so y is this  ?, cant tht be a bug ?
 any answers ?

cheers.

---

### Post by ubernoob on 2006-04-16
it's cause when you can press ctrl+alt+del or hit the power button, you have physical access to the computer. You can run terminals from whereever you want, and you don't want nonprivileged users to reboot your system.

---

### Post by index_0@ya.com on 2006-04-16
tok ... 
since i dont have a lan here to work with different terminals , 

let me ask u a question , 

wht if somebody passes clt+alt+del sequence (if tht's possible!) thru a remote shell  to the server .. ? 
will the server reboot ?

cheers, 
thx for ur reply

---

### Post by bishwo on 2006-04-16
It ,the protection, is surely only meant for remote logins.cuz, there is no protection against the power button..what sieqs me is why does it the protection in recovery mode.

---

### Post by ubernoob on 2006-04-16
you can't pass ctrl+alt+del trough a terminal in a way that reboots the system.

recovery mode is single user mode. (correct me if i'm wrong). A singel user is root and can reboot.

---

