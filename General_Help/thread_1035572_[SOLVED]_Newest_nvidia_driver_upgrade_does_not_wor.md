---
title: "[SOLVED] Newest nvidia driver upgrade does not work."
date: 2009-01-09
forum: General Help
---

### Post by Wylkar on 2009-01-09
Hi I have a hp pavilion dv9000 and the latest nvidia upgrade does not work and I have to work in default graphics mode. Is there any way to fix this problem or downgrade?
Thanks

---

### Post by mikewhatever on 2009-01-10
Uninstall the latest driver, I guess.:P

---

### Post by DeMus on 2009-01-10
> **Wylkar said:**
> Hi I have a hp pavilion dv9000 and the latest nvidia upgrade does not work and I have to work in default graphics mode. Is there any way to fix this problem or downgrade?
Thanks


I'm not 100% sure this will work but you could give it a try:
In the Synaptic Package Manager you can install a program called EnvyNG:
System | Administration | Synaptic Package manager.

After installation you can find a link in:
Application | System Tools

Start it, choose nVidia as your driver card and it will automatically download and install the latest driver for you.

After a re-boot it should work, but as I said there is no 100% guarantee since I don't know what you did and what happened when you did it.

Success.

DeMus

---

### Post by drs305 on 2009-01-10
You don't say what version of ubuntu you are using. In intrepid, you can try going to System > Administration > Hardware Drivers and look at the available versions. You will probably see several to select from. Choose an earlier version (lower number) and see if that works for you.

---

### Post by Wylkar on 2009-01-10
mikewhatever and drs305, I have tried both your solutions and neither has worked. I also tried reinstalling all of the old versions of the updated packages as well. DeMus I will try your suggestion.
Thank you all for your replies.

---

### Post by Wylkar on 2009-01-10
when I try EnvyNG I get the error message:
 +--------------------------------------------------------+
 |    Error:                                              |
 |                                                        |
 |    EnvyNG has detected that the headers for            |
 |    your kernel are missing and cannot be installed     |
 |                                                        |
 +--------------------------------------------------------+

I do not know how to resolve this error. Any help would be appreciated.
Thanks

---

### Post by Wylkar on 2009-01-11
I figured out the problem after looking at other threads. I was using an outdated kernel, so the kernel headers were incorrect.

---

