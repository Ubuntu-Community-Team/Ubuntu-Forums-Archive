---
title: "linux-kernel-headers"
date: 2006-09-13
forum: Desktop Environments
---

### Post by yaauu on 2006-09-13
Hi!

The "configure" script of Xilinx drivers [1] uses /usr/include/linux/version.h to figure out the current kernel version. In Ubuntu Dapper, that file says 2.6.11 while the real kernel version is 2.6.15. Actually, that file is modified by the linux-kernel-headers package. The problem is that in Dapper that package's version is 2.6.11.2 (seems outdated?), while many packages depend on it (ie. g++).

I'm gonna try to "lie" the "configure" script by changing by hand /usr/include/linux/version.h... but shouldn't that package be something like 2.6.15 or something like that in Dapper?

Thank you so much

[1] [http://www.xilinx.com/xlnx/xil_ans_display.jsp?iLanguageID=1&iCountryID=1&getPagePath=22648](http://www.xilinx.com/xlnx/xil_ans_display.jsp?iLanguageID=1&iCountryID=1&getPagePath=22648)

---

### Post by anaconda on 2006-09-13
Have you installed the linux-kernel-headers for your new kernel?

OK. I am not sure, but I think that in ubuntu you have to install them separately??

---

### Post by yaauu on 2006-09-13
what do you mean? I have installed "linux-kernel-headers", "linux-headers-2.6.15-26", "linux-headers-2.6.15-26-386", "linux-headers-386", "linux-source", "linux-source-2.6.15"... 

The problem is that while dapper's kernel is 2.6.15, linux-kernel-headers package's version is still 2.6.11, so /usr/include/linux/version.h says UTS_RELEASE "2.6.15".

I mean, maybe I'm missing something :-? but, if you have dapper and gcc for example installed, could you check your /usr/include/linux/version.h file?

Thank you

---

