---
title: "I am having trouble configuring smtp in Evolution"
date: 2008-12-27
forum: General Help
---

### Post by Lukasz Tarkowski on 2008-12-27
I am having trouble configuring smtp in Evolution,  sometimes they say port 465 is needed to be used, not port 25 hmm.  I don't see an option to change the port?

---

### Post by eBoxNet on 2008-12-27
you have to use ssl connection in order to make use of port 445 for smtp,find any secure connection related option and enable it.

(sorry can't remember where exactly it is to tell you but i think that i gave you a hint to find it)

---

### Post by jerome1232 on 2008-12-27
To specify ports in evolution you just tack it on the end of the address.

ie smtp.mail.server:445

---

### Post by Lukasz Tarkowski on 2008-12-27
I just did my.inbox:465 and it has worked.
Thank You jerome1232 :)

---

### Post by pstefanini on 2008-12-27
I haz the same problem some time ago, couldn't get it working.  My solution was to use Thunderbird instead.  I just tried though and don't understand the ssl advice.  Adding the port number to the outgoing address didn't work for me.  Phil

---

### Post by Lukasz Tarkowski on 2008-12-28
I understand the ssl thing,  Gmail needs it :D
I also know how to use ports in Evolution Thanx to that person :D

---

### Post by dcstar on 2008-12-28
> **pstefanini said:**
> I haz the same problem some time ago, couldn't get it working.  My solution was to use Thunderbird instead.  I just tried though and don't understand the ssl advice.  Adding the port number to the outgoing address didn't work for me.  Phil

Each of your individual Evolution account settings has a simple drop-down Security selection, all you do is select the "SSL Encryption" option if you need to use it.

---

