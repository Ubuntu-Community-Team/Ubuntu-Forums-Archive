---
title: "Dialup Connection Monitor"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Hexx on 2006-07-10
Well I've been successful in getting my dialup modem to work on Ubuntu.

However, having a tray icon in Windows that let me monitor my connection (speed, time, etc) was really helpful, so I tried adding Modem Monitor to my panel, but it lacks some features, such as the speed I've connected at. Not only that, but it skyrockets my CPU usage up to 100%! I have no idea why this happens?! Does it happen to anyone else?

Are there any applets I can get that will let me monitor my speed and duration of my connection?

---

### Post by chuckman78 on 2006-07-10
If you are using Gnome, you could try gnome-ppp, Find it in Synaptic.

Regards,

Carlos.

---

### Post by polka on 2006-07-10
> **Hexx said:**
> Well I've been successful in getting my dialup modem to work on Ubuntu.

However, having a tray icon in Windows that let me monitor my connection (speed, time, etc) was really helpful, so I tried adding Modem Monitor to my panel, but it lacks some features, such as the speed I've connected at. Not only that, but it skyrockets my CPU usage up to 100%! I have no idea why this happens?! Does it happen to anyone else?

Are there any applets I can get that will let me monitor my speed and duration of my connection?

I use gkrellm . It can be customized to monitor any of several components including dialup modem.

audo apt-get install gkrellm

Good luck 
Jerry

---

### Post by Fittersman on 2006-07-10
how did you get your modem to work man???? I have tried alot of stuff to get mine to work but its still not working.... where did you find what you need to get it to work?

---

### Post by Hexx on 2006-07-10
> **Fittersman said:**
> how did you get your modem to work man???? I have tried alot of stuff to get mine to work but its still not working.... where did you find what you need to get it to work?

I followed the instructions in the wiki [[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)]. I have a modem that uses the Lucent drivers, so it was pretty easy actually.

---

### Post by Hexx on 2006-07-11
> **chuckman78 said:**
> If you are using Gnome, you could try gnome-ppp, Find it in Synaptic.

Regards,

Carlos.

Downloaded gnome-ppp, works like a charm. Thanks!

---

### Post by Fittersman on 2006-07-12
how do you know if your useing gnome?

---

### Post by tonyr1988 on 2006-07-12
> **Fittersman said:**
> how do you know if your useing gnome?
Ubuntu = GNOME
Kubuntu = KDE
Xubuntu = XFCE

They can be changed, but those are the defaults.

---

