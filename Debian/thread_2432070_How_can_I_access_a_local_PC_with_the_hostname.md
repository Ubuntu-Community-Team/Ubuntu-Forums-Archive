---
title: "How can I access a local PC with the hostname?"
date: 2019-11-26
forum: Debian
---

### Post by crilawar on 2019-11-26
Hello, I am not an expert and I already have days of trying to access a **Debian PC** on a local network (not internet) **with the hostname and not with the IP.**

The issue is as follows:
I need to use [**Radicale **]("https://github.com/Kozea/Radicale/wiki/Simple-installation")to synchronize contacts and calendars, I just want to do it on a local network, between my laptop and my Android.

The problem is that I connect to several Wi-Fi during the week and **the laptop IP always changes**, so I need to know if it is possible to access the Debian laptop with just the hostname.

Thank you

---

### Post by uRock on 2019-11-26
Moved to ***"Debian"*** sub-forum.

---

### Post by Tadaen_Sylvermane on 2019-11-27
Many tutorials suggest just typing in a machines hostname to target it. That simply won't work unless the ip is added to the hosts file of the connecting machine or a private dns server, and with a changing ip that can be an issue. Your best bet is a static ip on devices as well as a private dns server. Can't always edit a hosts file on all devices, easily anyway. Bind is easy to set up, mine is working wonderfully and I simply followed the Ubuntu wiki. The config files are the same as Debian so it should work easy enough.

---

