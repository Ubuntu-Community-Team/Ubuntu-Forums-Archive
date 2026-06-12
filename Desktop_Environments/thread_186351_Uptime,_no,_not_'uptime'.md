---
title: "Uptime, no, not 'uptime'"
date: 2006-06-01
forum: Desktop Environments
---

### Post by SuperMike on 2006-06-01
What's the command to find an application (daemon, service, pid, whatever you want to call it) uptime, not the OS uptime you get with the 'uptime' command?

I was wanting to generate some reports on how long several pieces of a web application have been up and running.

---

### Post by Kronoz on 2006-06-01
If you use the command 'time' as a prefix to a command before running it when it terminates it will print sys time + real time + something-else-that-i-can't-remember but I guess you want to read how long they have been up while they are still running.

---

