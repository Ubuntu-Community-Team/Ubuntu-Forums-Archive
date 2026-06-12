---
title: "Locks up after boot if nobody logs in"
date: 2011-08-02
forum: Desktop Environments
---

### Post by bsnelson on 2011-08-02
I have a bit of a different problem from the usual. I've loaded 10.04.2 LTS desktop and it's still mostly stock. I have turned on remote desktop, and it works if I log in on the console first. 

The problem is if I *don't* log in to the console. When I boot the machine, I have to log in within about 15 minutes or so; if I don't, the machine becomes (mostly) unresponsive. It still replies to pings, but ssh attempts hang. Also, if I go to the console at that point, the console is completely unresponsive (no video, keyboard num/caps/scroll lock toggles don't toggle the lights etc). The CPU fan is also in high gear at this point, suggesting something's looping. 

This morning, I rebooted and quickly logged in through ssh and did a "top", hoping that if it did start looping, maybe the CPU offender(s) would show as the last update before I lost my ssh session; no luck, it was still 99% idle when it froze up. 

As I said earlier, if I log in on the console within 10-15 minutes of booting, everything is fine, it'll sit for days waiting for VNC logins, ssh, whatever. 

Any ideas? Thanks in advance,

Brad

---

