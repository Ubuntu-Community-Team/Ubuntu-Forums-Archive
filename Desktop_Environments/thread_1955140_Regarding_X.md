---
title: "Regarding X"
date: 2012-04-09
forum: Desktop Environments
---

### Post by vijay496 on 2012-04-09
Hi all, 

  I am new bie to Ubuntu. I am using Ubuntu 11.10  when I tried to forcibly kill the X server from my process it again starts  
and prompts me a login screen how this is happening.  Please help me  
vj         2383   908  0 15:01 tty2     00:00:00 -bash 
root      3054     1  0 15:04 ?        00:00:00 lightdm 
root      4395  3054 14 15:12 tty7     00:21:50 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -noliste 
vj         4498     1  0 15:12 ?        00:00:00 /usr/bin/gnome-keyring-daemon --daemonize --login 
vj         4508  3054  0 15:12 ?        00:00:00 /usr/bin/gnome-session --session=ubuntu 

Kill 4395 


Thanks, 
Vijay

---

### Post by grahammechanical on 2012-04-09
I may be wrong but I think that we need the X-Server to be running otherwise we would not have a working operating system.

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

So, please explain why you want to kill the X-Server process.

Regards.

---

### Post by kiirokurisu on 2012-04-10
In Ubuntu X is started by lightdm which in turn is a service controlled by Upstart. When you kill X, Upstart detects this and starts X again. If you run ```
sudo stop lightdm
```, this will probably stop X and also prevent it from starting again.

---

### Post by vijay496 on 2012-04-11
So lightdm is the one responsible for restarting my X, Could you please suggest me how can I start only my own application ie along with X at startup. so that it again restarts when it is got killed just like X(i.e restarting).

Thanks.

---

### Post by roelforg on 2012-04-11
> **vijay496 said:**
> So lightdm is the one responsible for restarting my X, Could you please suggest me how can I start only my own application ie along with X at startup. so that it again restarts when it is got killed just like X(i.e restarting).

Thanks.

Watchdog+xinit?

---

### Post by vijay496 on 2012-04-11
hi roelforg  could you please elaborate I am not specialist in this part ...

---

