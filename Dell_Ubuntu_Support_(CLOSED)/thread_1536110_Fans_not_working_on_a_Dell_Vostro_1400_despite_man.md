---
title: "Fans not working on a Dell Vostro 1400 despite many tries"
date: 2010-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 0x414141 on 2010-07-21
Hello, 

  I have a Dell Vostro 1400 with Lynx (32 bits) and my fans dont work. I have tried DellFanD and Gkrellm. There does not appear to have any valid archive for gkrellm and DellFanD did nothing (result was always -1).

Here is my uname -a result (I assume it helps)

> 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
Could you please give me some pointers?

---

### Post by 0x414141 on 2010-07-25
A little *bump* for hope...

My cpu is most of the time above 60...

---

### Post by vangop on 2010-07-26
take a look at the i8kutils package.
It has i8kfan/ctrl/mon utilities that can control the fans. Although I didn't manage to config it to run properly on boot, it seems to work if run manually.

---

### Post by 0x414141 on 2010-07-27
There are no valid packages for Ubuntu Lynx for i8kutils for the fan control. Either that or the i8kutil that i used (from apt-get) does not have that plugin.

Thanks for the try.

---

### Post by PRC09 on 2010-07-27
If you arent running the latest bios from Dell there is a note in the Fixes and Enhancements that says Added enhancements for thermal control.Just a thought.......






[http://support.dell.com/support/downloads/driverslist.aspx?os=BIOSA&catid=-1&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=-1&servicetag=&SystemID=VOS_N_1400&hidos=WLH&hidlang=en&TabIndex=&scanSupported=False&scanConsent=False](http://support.dell.com/support/downloads/driverslist.aspx?os=BIOSA&catid=-1&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=-1&servicetag=&SystemID=VOS_N_1400&hidos=WLH&hidlang=en&TabIndex=&scanSupported=False&scanConsent=False)

---

