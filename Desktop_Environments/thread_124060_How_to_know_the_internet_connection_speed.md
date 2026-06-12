---
title: "How to know the internet connection speed?"
date: 2006-01-31
forum: Desktop Environments
---

### Post by genbie on 2006-01-31
Hi,

I am having a problem where my actual connection is allegedly 8MB/sec, but all the test sites show it as maximum 2MB/sec :mad:  Is there a command that can verify my 8MB/sec connection speed or something close to it like 6MB/sec or 7MB/sec? My modem is Alcatel Speedtouch USB modem which should handle speeds up to 8MB under linux AFAIK. 

Thanks.

---

### Post by kingsidy on 2006-01-31
you can test it using those websites like dslreports.com. as far as the speed goes lets say that the max down speed it 1.5Mbps, that means when you download the theoretical speed you can get it about 1.5M/8 k byte per seconds. re member the units (bits vs bytes).

---

### Post by BigDeal on 2006-01-31
Can the actual speed be measured like DUmeter in windows?

---

### Post by awi on 2006-01-31
there are a few desklets ([http://gdesklets.gnomedesktop.org/index.php](http://gdesklets.gnomedesktop.org/index.php)) that show your network interface traffic. There is also modules for [COLOR="SeaGreen"]gxmms[/COLOR] that does the same.

---

### Post by dcstar on 2006-01-31
[QUOTE=kingsidy]you can test it using those websites like dslreports.com. as far as the speed goes lets say that the max down speed it 1.5Mbps, that means when you download the theoretical speed you can get it about 1.5M/8 k byte per seconds. re member the units (bits vs bytes).[/QUOTE]
If you are referring to ADSL connections, the "wire rate" is always ~15% more than any usable throughput you can **ever** get due to various overheads.

---

### Post by genbie on 2006-02-02
Many thanks for the replies guys.

The new testing sites also gave me the usual 2MB/sec. speed. Thanks for pointing out the difference between byte and bit but I had already known about it.

I installed the gDesklet but it did not show the speed on ppp0 for some reason.

So I finally tried the wget command to download a big file from one of Ubuntu's servers and the fastest rate was something like 380-400 KB/sec which is roughly 3 times what I used to get with a 2MB/sec connection (i.e. [400KB/sec with an 8MB/sec connection] vs. [130KB/sec with a 2MB/sec connection]). So I guess my linux and Alcatel modem are recognizing the faster connection but they are not displaying the info.

Thanks again.

---

### Post by awi on 2006-02-02
This is an old application, that a friend of mine made, a long time ago, when we had only dial-up modem internet connection (gooood times :)  ).

[http://www.pla.net.py/home/oliver/gpppkill/](http://www.pla.net.py/home/oliver/gpppkill/)
[http://www.pla.net.py/home/oliver/gpppkill/screenshots.html](http://www.pla.net.py/home/oliver/gpppkill/screenshots.html)

---

