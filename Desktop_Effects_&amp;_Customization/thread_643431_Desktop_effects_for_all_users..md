---
title: "Desktop effects for all users."
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by Teddy_P on 2007-12-17
I can not get desktop effects for all the users on any of the 3 computers I have. Just one at a time. Is there a way to have everyone get the desktop effects?


Teddy

---

### Post by brett611 on 2007-12-18
If you have an ATI card try this link 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I had the same issue and this fixed it

---

### Post by Teddy_P on 2007-12-18
both computers say that "your hardware does not need any restricted drivers"
I will check tonight to see what card is in all of them.


Thanks
Teddy

---

### Post by mike868y on 2007-12-18
Go to System>Admininstration>Restricted Driver Manager and deselt the enabled box.. this shoudl disable the use of the restricted driver.. When i tried using the restricted driver i could not get desktop effects working either

---

### Post by Teddy_P on 2007-12-24
One one of the computers i do not have it enabled. 

I can not figure out which card I have in the computer. Is there a way to look it up?



Teddy

---

### Post by Forlong on 2007-12-26
> **Teddy_P said:**
> I can not get desktop effects for all the users on any of the 3 computers I have. Just one at a time. Is there a way to have everyone get the desktop effects?
No, that's not possible. Compiz is still running on the first logged in user's X-server.

Plus, you'd need independent X-servers, which GNOME doesn't set up for every user.

---

