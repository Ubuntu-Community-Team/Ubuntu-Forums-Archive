---
title: "No wifi after hibernate: E1505N"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by cody50 on 2007-06-27
I have noticed that after I hibernate with my E1505N upon wakeup there is no wifi. If I click on the network manager to choose networks it only gives wired as an option. I tried the Fn+ wifi key on the keyboard but that didnt seem to do anything. anyone have any ideas?

---

### Post by highlighter on 2007-06-27
I'm not to certain, but did you check the restricted driver afterward to see if it was still enable?

---

### Post by cody50 on 2007-06-28
That is really odd. I just tried it again and It worked fine. If it happens again i'll be sure to see if the driver is still enabled and I'll repost the results also with other info that may be of use.

---

### Post by binkl on 2007-06-29
Yeah, I have the same problem. It connects intermittently after suspend or hibernate. I've found that disabling and re-enabling the wireless configuration in NetworkManager fixes the problem, but it's a pain. I'll post back if I find an easier solution.

binkl.

---

### Post by neptho on 2007-06-30
If you have an Intel 3945, add "ipw3945" to the MODULES_WHITELIST in the /etc/default/acpi-support file.

---

