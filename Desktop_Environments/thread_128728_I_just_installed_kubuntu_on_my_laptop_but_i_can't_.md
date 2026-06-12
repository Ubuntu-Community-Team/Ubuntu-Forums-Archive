---
title: "I just installed kubuntu on my laptop but i can't find firefox!"
date: 2006-02-12
forum: Desktop Environments
---

### Post by Programmer on 2006-02-12
Someone can tell me how do i install it ?
"sudo apt-get install firefox" and "sudo apt-get install mozilla-firefox" don't work!

Thanks.

---

### Post by eriefisher on 2006-02-12
You should be able to goto Kmenu>internet>firefox. No?

eriefisher

---

### Post by Programmer on 2006-02-12
After googling around i found that i must unmark some stuff in "/etc/apt/sources.list" before i do "apt-get update"
now, after the update i tried "apt-get install firefox" again and it worked.

But now i have another problem, it installed firefox version 1.0.7 instead of 1.5 how do i update it ?

---

### Post by rudiz on 2006-02-12
Look here:

[https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29%7C%28new%29%7C%28version%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29%7C%28new%29%7C%28version%29)

---

