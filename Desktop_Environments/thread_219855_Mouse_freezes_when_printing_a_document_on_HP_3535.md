---
title: "Mouse freezes when printing a document on HP 3535"
date: 2006-07-20
forum: Desktop Environments
---

### Post by rodrigo666 on 2006-07-20
Greetings,

Everytime I go print some document with my HP Deskjet 3535 the mouse freezes just as the sheet gets ink.

The worst part is that it does not come back alive unless I reboot the system.

This really bothers me, so if anyone out there could help me, I'll apreciate.

Thanks.

---

### Post by avtolle on 2006-07-20
Are the printer and mouse both USB devices? If so, are they somehow sharing the same USB port? Sounds like the printer takes the port over, and won't give it back, so to speak.

---

### Post by rodrigo666 on 2006-07-20
Yes they both are USB, sorry for not mentioning that.

But I don't think they are sharing the same USB slot.

I mean, each one is plugged in a diferent slot. Beside that I have a HP Scanner plugged in another one and theres a fourth slot empty (and the ones in front of my - don't know how to call it in english - PC case)

---

### Post by avtolle on 2006-07-20
The reason I brought it up was I have several USB 'slots' but in reality only two USB ports, thus when using an external USB CD-RW drive, my printer goes crazy. I investigated, and found out that even though each was in a different "slot", they were in fact sharing the same port. 

You might want to go to a terminal and type lspci -v and see what the output of that command is (I think it's right, I'm a fairly new user). That will hopefully let you know how many USB ports your system has, among other things.

---

