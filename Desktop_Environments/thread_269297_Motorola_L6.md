---
title: "Motorola L6"
date: 2006-10-01
forum: Desktop Environments
---

### Post by Chxta on 2006-10-01
A friend of mine uses a motorola L6 and (on my recommendation) installed Dapper Drake. Unfortunately, it refuses to recognize his phone- a Motorola L6. It sees it as a "e398 GSM phone" and doesn't see it as a modem. Even the 'dmesg | grep USB' command doesn't locate the phone all I get about the phone is ACM stuff whats that about even when I try auto detect it doesn't even work. Is there anyway I can make it find the phone?

---

### Post by gborzi on 2006-10-01
I have a Motorola C350. Once I connect it with the cable to the PC, ubuntu loads the cdc_acm module and creates a device for it, i.e. /dev/ttyACM0. I can use that device as a modem device, that is to say for an internet connection. What do you mean when you write that "all I get about the phone is ACM stuff" ?

---

### Post by rattusdatorum on 2006-10-05
also have a L6, but I wanna just want access to its data, but nothing worked so far (it is detected with lsusb, but not mounted and kmobile didn't worked either.)

---

### Post by gborzi on 2006-10-05
@rattusdatorum:
Have you tried [moto4lin]("http://moto4lin.sourceforge.net/wiki/Main_Page")  ? It worked fine with my C350. There is an Howto in the forums and .deb files are available at the moto4lin site.

Regards.

---

### Post by Raval on 2007-12-09
> **rattusdatorum said:**
> also have a L6, but I wanna just want access to its data, but nothing worked so far (it is detected with lsusb, but not mounted and kmobile didn't worked either.)

DId you ever get your phone to work?

---

### Post by rattusdatorum on 2007-12-12
nope, but I didn't continue to try, had a big Mac in my office ;)

---

### Post by Raval on 2007-12-12
> **rattusdatorum said:**
> nope, but I didn't continue to try, had a big Mac in my office ;)

Oh great! not only does my frustration continue after your reply but now I'm hungry:(

---

