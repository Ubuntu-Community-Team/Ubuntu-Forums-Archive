---
title: "hibernate in 11.10"
date: 2012-04-19
forum: Desktop Environments
---

### Post by nirensinha on 2012-04-19
Ever since I upgrade to 11.10, i am not able to successfully hibernate or at time suspend my desktop. I am using AMD with nvidia drivers.

Hibernate was working fine in 11.04 only with tuxonice but now it fails while saving the pages. I have tried lot of things, kernel from ubuntu repository, tuxonice, compiled my own kernel, uswsusp but nothing works.

This is really frustrating as I always hibernate my desktop. Every day my computer freezes while hibernating and I have to hard stop it. I have done hard stop so many time that now my hard disk is showing errors. I have completely given up and need some help.

Ubuntu is one of the best Operating System out there and I have been using it for last 5 years. I dont want to switch to any other flavor. 

Please help. Thank you

---

### Post by Toz on 2012-04-23
> **nirensinha said:**
> Ever since I upgrade to 11.10, i am not able to successfully hibernate or at time suspend my desktop. I am using AMD with nvidia drivers.
Have you installed the proprietary drivers for your nvidia card? Open a terminal window, type in the following command, and post back the results:
```
sudo lspci -vnn | grep -A10 VGA
```

> Hibernate was working fine in 11.04 only with tuxonice but now it fails while saving the pages.
Are you getting error messages? If so, what are they?

> I have tried lot of things, kernel from ubuntu repository, tuxonice, compiled my own kernel, uswsusp but nothing works.

This is really frustrating as I always hibernate my desktop. Every day my computer freezes while hibernating and I have to hard stop it. I have done hard stop so many time that now my hard disk is showing errors. I have completely given up and need some help.

Ubuntu is one of the best Operating System out there and I have been using it for last 5 years. I dont want to switch to any other flavor. 

Please help. Thank you

Can you also post back the contents of **/var/log/pm-suspend.log** and **/var/log/dmesg**, along with the results of the following commands:
```

sudo dmidecode -s system-manufacturer
sudo dmidecode -s system-product-name
cat /proc/cmdline
cat /etc/fstab

```

And finally, how much RAM does this computer have?

---

