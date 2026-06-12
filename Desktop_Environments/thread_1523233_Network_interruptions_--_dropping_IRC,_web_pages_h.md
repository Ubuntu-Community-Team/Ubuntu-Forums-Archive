---
title: "Network interruptions -- dropping IRC, web pages half-renderd"
date: 2010-07-03
forum: Desktop Environments
---

### Post by todb on 2010-07-03
Hi all. I just cannot figure this out. About two or three times a day, I will briefly loose an IRC connection, only to reconnect a second or two later. Also, web pages have a tendency to only partially render -- sometimes an F5 takes takes care of it, sometimes more than one. This is Ubuntu 9.10, Karmic.

This does not occur with any other computer in the house.

Firefox or Chrome, both behave badly. Adblock on or off. It's a laptop with wlan0 (Intel) and eth0 (RealTek), but changing interfaces doesn't seem to matter.

Some network functions appear to have no problem -- I stream somafm all the time, and never have an interruption there, nor do very long World Cup video streams. Just IRC and web. Maddening.

The kicker is, this computer dual boots. I'm not often booted to Windows 7, but when I am, I don't notice any of this web page partial rendering at all.

I am pretty decided that it's a network driver issue, and have stared at Wireshark captures, but don't see anything obvious there. Is there a comprehensive network driver troubleshooting guide for Ubuntu? I'm about ready to upgrade to 10.4 in a vain hope the problem will go away, but I can't find any reason to believe this.

---

### Post by todb on 2010-07-10
A) Okay, I do know how to spell "rendered"

B) Man, I wish I had a decent plan for troubleshooting this. The IRC drops are annoying to other people, so really, I don't care all that much. However, the half-rendered web pages are really irritating.

I upgraded to Ubuntu 10.4, which worked out much better than I expected, but the problems remain. FWIW, I'm on a Sager laptop, because for some reason my employer is totally hot on Sager. :)

---

### Post by todb on 2010-09-07
So, I believe I solved the problem:

    # Hey maybe this will fix my stack? WTH is Ubuntu doing anyway?
    net.ipv4.tcp_wmem = 4096 16384 131072
    net.ipv4.tcp_rmem = 4096 87380 174760

This is probably wrong-ish for a reasonably-fast broadband connection, but my reddit timeouts have all but disappeared. Hooray!

---

