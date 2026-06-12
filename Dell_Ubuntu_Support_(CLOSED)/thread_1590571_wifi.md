---
title: "wifi"
date: 2010-10-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tripsus on 2010-10-08
i ve a studio 1558 laptop. i recently installed ubuntu 10.4.
i am not able to use wifi in ubuntu as mine function key does not work in ubuntu. can any one help me with the command to on wifi in ubuntu and more how do i confihure settings in wifi coz windows atomatically checks for settings can i do the same in ubuntu.Any help or suggestion is heartily welcoomed:)

---

### Post by ibtkm on 2010-10-08
i think you didn't install your wifi driver.
go => system-administration-hardware drivers.
don't forget to configure your repo.for installing hardware driver you should have a repo.

---

### Post by Peter09 on 2010-10-08
If you still have problems can you post the output of the terminal commands
 
```
ifconfig
```
and
```
lshw -C network
```
 
Note: it is also important to connect to the internet (hardwired) and do an upgrade straight after you install Ubuntu as it will download any drivers that it needs, and check in your System->Administration Menu->Hardware to see if any drivers need enabling.

---

### Post by tripsus on 2010-10-19
Thanks:) for ur support I tried this but unfortunately it didnt work. Now i have installed ubuntu 10.10. I am trying to usb broadband like tata phton but it is also not working i am not finding any way to connect to internet. i have already edited the vpn connections of broadband.your suggestions are welcome.:rolleyes::rolleyes::rolleyes:

---

