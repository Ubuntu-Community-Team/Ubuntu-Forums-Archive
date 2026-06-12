---
title: "Inspiron 1525 - Drivers Not Working"
date: 2010-03-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by btthead on 2010-03-07
I did the "sudo lshw -C Network" thing and I got UNCLAIMED

I did as instructed with the ndswrapper (or what ever it is called) and it said that my driver was not a valid driver

what can I do?

this is on ubuntu 9.10 btw

---

### Post by mikewhatever on 2010-03-07
Can you post the full output of that command, instead of telling what it was. Chances are, you don't need ndiswrapper at all.

---

### Post by btthead on 2010-03-08
sorry I can't, b'cus I can't get anything from ubuntu onto the internet : (

---

### Post by bkratz on 2010-03-08
> **btthead said:**
> sorry I can't, b'cus I can't get anything from ubuntu onto the internet : (

If you do

```
lspci >> ~/Desktop/lspci.txt
```

( that is LSPCI in lowercase, D in uppercase) it will create a file on your desktop which will give the needed info and can be transferred via thumbdrive to whatever you are posting with.

This will give the output of what is connected to you pci bus.

---

### Post by anthonyrossbach on 2010-03-09
I have the same computer as you, and the error for me was fixed on 9.10. To get mine working I just lan connected to the Internet and upgraded to 9.10 and the errors where fixed for this!

---

