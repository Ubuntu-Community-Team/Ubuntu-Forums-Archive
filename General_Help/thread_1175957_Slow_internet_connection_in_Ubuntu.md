---
title: "Slow internet connection in Ubuntu"
date: 2009-06-01
forum: General Help
---

### Post by nailo on 2009-06-01
Hi, all. I'm on Ubuntu for the first time in ages, and having some rather frustrating problems with my internet connection. I'm not sure if this is the right place to ask (new to the forums, etc), but I figured I'd give it a shot. Ever since my install of Ubuntu, my internet connection has been remarkably slow. I'm using an Acer Aspire 6930, and originally installed Ubuntu 8.10, which my wireless worked with out of the box. However, upon testing my speed with even a wired connection, my internet speed isn't nearly that of what I got in windows (windows vista, 7 beta build 7000). For all that I like about running ubuntu again, this is really giving me a problem. I've tried swiftfox and opera browsers in addition to the stock firefox build, and have played with a lot of the settings in the config files (disabling ipv6 seems to be a common problem), but to no avail. I'm now on 9.04 jaunty, thinking the upgrade might fix the issue, but my connection isn't faster. For reference, I'm using an Ambit Orion 3000 cable modem, and my ISP is Roadrunner (yeah -_-). Any help would be appreciated, thanks.

---

### Post by madverb on 2009-06-01
Could use something like Wireshark to see if it's losing lots of packets?

---

### Post by nailo on 2009-06-01
Dunno, I doubt if it's loss of packets, but I'll check and see if I'm dropping any, and post results. Thanks.

---

### Post by nailo on 2009-06-01
Hmm. I've been pinging my router for 5 minutes or so, and only lost one packet overall (out of a few hundred).

---

### Post by madverb on 2009-06-01
You shouldn't lose any pinging something locally

---

### Post by DVANDERM on 2009-06-01
Try: 'sudo iwconfig wlan0 rate 54M' in a terminal. See if that helps. (leave out the ' )

---

### Post by nailo on 2009-06-02
That didn't seem to help, thanks though. Any other suggestions?

---

