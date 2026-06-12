---
title: "SLMODEM - gnome-ppp/kppp"
date: 2006-01-03
forum: Desktop Environments
---

### Post by p0liX on 2006-01-03
I installed ubuntu on my Dell Inspiron 1100 laptop.  Everything works good except gnome-ppp or kppp.

I installed the latest 2.6.10-686 kernel, with the slmodem drivers (my modem is an AC'97 modem), i setup my ISP account on the ppp device under the networking options and when i activate it there it comes up and connects fine.

But when i use gnome-ppp or kppp, it connects but quickly disconnects, saying carrier signal was lost...retrying.  When i watch the log i can see it connecting and sending login information, but it seems to be sendign the information 3 times  in a row.  The information in the settings of both are correct, i verified several times and even tried a different account.

Is anyone familiar with this problem and if so, is there a way to fix it so I can use gnome-ppp or kppp to connect with instead of manually activating the ppp interface?

---

### Post by digitalkarabao on 2006-01-03
try (re)installing slmodem from the repositories using synaptic.

---

