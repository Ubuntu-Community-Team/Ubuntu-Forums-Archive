---
title: "ssh and process?"
date: 2010-02-27
forum: Desktop Environments
---

### Post by vksingh on 2010-02-27
Hi,

I have a small confusion. When I do ssh to my server from my machine and start a download with the following command:

$ wget  xyz

Then if I close my ssh window, will the process of wget run? If not, How should I run a process in server in background so that even I close the shell, Process still runs.

Thanks,

Vivek

---

### Post by jswoods7 on 2010-02-27
Use screen (man screen) or nohup (e.g. nohup wget abc &)

---

