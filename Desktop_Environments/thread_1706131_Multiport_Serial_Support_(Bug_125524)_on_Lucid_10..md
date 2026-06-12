---
title: "Multiport Serial Support (Bug 125524) on Lucid 10.04"
date: 2011-03-13
forum: Desktop Environments
---

### Post by uhu_maotouying on 2011-03-13
Hi friends,

can I bother you with the ever ongoing story on Bug 125524 ?

What would be your advice for someone like me with intermediate level of understanding Linux only : I would like to make the "8250.nr_uarts=6" boot option permanent with Kernel <= 2.6.32-29 on LUCID 10.04 .
And, sadly, compiling the kernel => 2.6.37-7 did not work for me ... 

I am confused by the number of options and advices.

Thanks ... uhu

---

### Post by uhu_maotouying on 2011-03-14
Finally I have found a patch I quite like :

[www.avalue.com.tw/support/download2.cfm?FILENAME=D...173pdf](www.avalue.com.tw/support/download2.cfm?FILENAME=D...173pdf)
FAQ Document No: S10015, Date: 2010/07/23
Model Name. EPS-AT270, Rev. A1

It works like this :

1. sudo gedit /etc/default/grub
2. edit the line : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash 8250.nr_uarts=6"
3. sudo update-grub
4. reboot
4. check whether it is working : sudo cat /proc/tty/driver/serial

Thank you, &#35874;&#35874;&#20320;&#20204; to our friends in Taiwan. uhu

---

