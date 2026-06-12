---
title: "Missing hibernate &amp; suspend"
date: 2010-10-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by donkeyotay on 2010-10-24
Morning All,
[LEFT]Yesterday I added a 2GB RAM stick to a Dell D520  laptop. The upgrade seemed to go without a hitch until I went to  hibernate the computer; Hibernate & Suspend are now missing. Everything else seems to be working correctly.
Any ideas gratefully received.
Donkeyotay
[/LEFT]

---

### Post by mörgæs on 2010-10-26
When hibernating the swap space receives the contents from memory for storage until the machine is waking up. 

This is just guessing: Could this be because now you don't have enough swap to accommodate all memory?

---

### Post by donkeyotay on 2010-10-26
I've allocated 2 GB swap space...how can I find out if this is enough please?
Donkeyotay

---

### Post by mörgæs on 2010-10-27
Basically you can just increase swap to 4 GB with Gparted, boot the machine and see if it works.

---

### Post by rainbow99984 on 2010-10-27
You can get similar performance by  System->Preference->Startup Applicatoin ->Option tab. select Automatically remeber running app when logout. this will gives you similar effect. 
but mind that hibernate,or this feature takes time at start up so wait for some seconds. I was having similar problem but when i update the nvidia x-server it works. don't know how nvidia x-server was related but that solve
you can try the first one at least for the time until you get what you want.

---

