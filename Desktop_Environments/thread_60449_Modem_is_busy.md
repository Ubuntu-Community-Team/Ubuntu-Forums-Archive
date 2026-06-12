---
title: "Modem is busy???"
date: 2005-08-27
forum: Desktop Environments
---

### Post by bvsciguy on 2005-08-27
I have used KPPP in an attempt to connect to the internet using my AOL account, I think. Now, when I try to connect to the internet I get a message that says that the modem is busy. Initially I thought that I just had chosen the wrong port, but it says that when I try to sign on using several different ports. What does it mean when it says that my modem is busy, are there multiple ports used to connect to the modem, can someone tell me how to make my modem "un-busy".
Thanks,
bvsciguy

---

### Post by OBnascar on 2005-08-27
I had the same problem with an external serial port modem but resolved it this afternoon. What worked for me was I just didn't give up on it and tried different settings, such as /dev/ttySO, /dev/modem, ect. over & over. I think one time I cleared everything out of the KPPP tool, rebooted, opened the KPPP tool, unplugged the external modem and plugged it back in again and re-entered my info. Someone told me to try that, not sure which helped.

Anyway, about two hours later I did a querry and it saw my modem. That is my story and I am sticking to it, LOL !

Don't know if this will be helpful to you or not...good luck.

---

### Post by OBnascar on 2005-08-27
Oh, someone will be sure to ask you what is your modem ? Internal, external USB, or external serial port ?

---

### Post by bvsciguy on 2005-08-27
It's an internal modem, Agere Systems AC'97, attached to COM4.

---

