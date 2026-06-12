---
title: "Modem configuring"
date: 2009-03-03
forum: General Help
---

### Post by jeff35 on 2009-03-03
I have just installed Ubuntu on my dell 4600. I installed inside windows xp. I have installed the linexant  .deb file. I think it is done right, I got a modem initialized feedback. 

Now I cant find the modem in the network area. how can I configure the wvdial. program? Im lost

---

### Post by NoReflex on 2009-03-03
Hello!

Usually I use Gnome PPP to configure modems - it's in the repos and it's easy to use.

Best wishes,
NoReflex

---

### Post by jeff35 on 2009-03-03
gnome ppp worked great, now i am having a problem with netzero, how do i link netzero interface with gnome ppp?

---

### Post by NoReflex on 2009-03-04
I'm sorry but I'm not familliar with NetZero - is it like a wireless provider with some dedicated USB modem?
I'm sure there's somebody here that has experience with it.
If it's a modem that you plug into your computer try to see if it's detected.
The commands that will help you establish that are : lspci, lsusb and tail /var/log/messages.
Good luck!

Best wishes,
NoReflex

---

### Post by jeff35 on 2009-03-05
I am downloading gnome ppp again looking for deb file, i messed up and reloaded ubuntu, netzero uses its own dialer, which likes to give u other access numbers that cost more. getting ready to check it out closer.

---

