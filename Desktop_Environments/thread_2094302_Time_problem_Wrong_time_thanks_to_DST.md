---
title: "Time problem: Wrong time thanks to DST"
date: 2012-12-13
forum: Desktop Environments
---

### Post by bxlion on 2012-12-13
Hi everyone, nice to make my first post. 

I'm currently running Ubuntu 10.04 LTS- the Lucid Lynx and my problem now is that even though it does know I'm in Puerto Rico and it's suppose to synchronize time. It has for some reason thought that an island in the Caribbean uses Daylights Saving time. We don't. So it's always one hour ahead.

I've tried to use "hwclock --show" and it does display the correct time. Any suggestion or additional info just ask.

---

### Post by dannyboy79 on 2012-12-13
have you tried the following suggestions?
[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by bxlion on 2012-12-22
Thanks for the website, sadly it's still not working.

I did follow it's suggestions and still my time is consistently one hour ahead of actual time. I tried using NTP servers, but it appears from troubleshooting that I have a routing/firewall problem since using "ntptrace $server" keeps timing out. 

What I find so odd is that even though the system's time and date settings has America/Puerto_Rico timezone it's incorrect from the actual puertorican time! :???:

---

### Post by dannyboy79 on 2012-12-22
not sure then, sorry

---

