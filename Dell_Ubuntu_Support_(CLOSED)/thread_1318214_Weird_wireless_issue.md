---
title: "Weird wireless issue"
date: 2009-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kboutsider on 2009-11-07
Hi, very new to Ubuntu as a matter of fact this is the first time i've ever used linux.  I have everything installed on my Dell Inspiron 1525 and the dual boot works great with my windows vista.  This issue i'm having is getting the internal wireless card to work.  I can get wireless but I have to use a no name usb wifi stick.  Here is the odd part the usb stick only works if I have the internal wifi switch turned on.  If someone can help it would be great cause it really sucks when I forget to toss the usb stick into my laptop bag.

Thanks
KB

---

### Post by eidaot on 2009-11-08
KB,  I'm using a 1525 also and the wireless worked flawlessly for me on the past 5 or so versions of Ubuntu.  What kind of wireless card did your laptop come with?  

You may need to install a restricted driver.  You can do so by going to System->Administration->Hardware Drivers.

Let us know the type of network card you have, if you open a terminal and type the following, it should let you know.
```
lspci
```

You'll see something similar to this in a big list.
```
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

---

### Post by kboutsider on 2009-11-08
It's a Dell 1395 but it's ok got it figured out.  Like you suggest I had to download the restricted drivers.  Works like a charm.

---

