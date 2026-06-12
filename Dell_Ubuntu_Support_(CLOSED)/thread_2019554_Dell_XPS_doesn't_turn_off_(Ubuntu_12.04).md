---
title: "Dell XPS doesn't turn off (Ubuntu 12.04)"
date: 2012-07-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Sapienso on 2012-07-07
Hi. My computer is a Dell XPS 1730, and I have had a problem since I installed 12.04. It  does not turn off, unless I apply for a few seconds the turn off button.  It does not reiniciate, either. 

I have done a number of things recommended in [www.ubuntu-es.org]("http://www.ubuntu-es.org"), the Spanish forums, but to no avail:

I have done things like installing   **wmshutdown** and **qshutdown**; also I have edited the grub file to modify the line that says 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

to add  "acpi=force", so that it ends up like: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force" 

It has not worked.Can anyone help me, please?[FONT=Ubuntu]


[/FONT]

---

### Post by mc4man on 2012-07-09
You've posted this in 3 different sub-forums which isn't a good idea, you should rectify that.

IF your Dell has a nvidia adapter, you are using the nvidia drivers AND on a 32 bit install then there is a known issue that might be affecting you.

If so there are 3 solutions that do work
1. switch to the nouveau driver
2. remove the 12.04 32 bit  install & use the 64 bit version
3. downgrade nvidia-current to nvidia-current_290.10-0ubuntu2_i386 package

reference bug I filed, unlikely to be specifically fixed, still applies to the latest nvidia (302.XX
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564)

---

### Post by Sapienso on 2012-08-01
> **mc4man said:**
> You've posted this in 3 different sub-forums which isn't a good idea, you should rectify that.

Thank you, mc4man. I will correct it. 

In fact, I was looking for my posts in order to provide the link of the post in which you solved the problem: 

[http://ubuntuforums.org/showthread.p...7&goto=newpost]("http://ubuntuforums.org/showthread.php?t=2020577&goto=newpost")

Thanks again,

---

### Post by Sapienso on 2012-08-01
I also posted the link in the Spanish forums: 

[http://www.ubuntu-es.org/node/167698](http://www.ubuntu-es.org/node/167698)

---

