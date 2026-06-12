---
title: "Optimization for Acer AOA110 / High CPU when browsing web"
date: 2020-10-27
forum: Desktop Environments
---

### Post by jankohrasko142 on 2020-10-27
Hello team, 

I installed xubuntu on an old "netbook" Acer Aspire One ZG5 with Intel Atom.
The OS overal works good, but there is a problem when starting and using web browser --> the CPU goes up to 100% and response is slow, it freeze, it needs time to load a web page. I tested with FF and Chromium.
I understand it is an old HW **but can you advise me some optimization steps?**
I installed XFCE.

Intel(R) Atom(TM) CPU N270   @ 1.60GHz, 1GB RAM
NAME="Ubuntu", VERSION="18.04.5 LTS (Bionic Beaver)"

All details and screenshots in attachment. 
Thank you.

---

### Post by ActionParsnip on 2020-10-27
Use a loghter web browser. 1Gb RAM will struggle with a very feature rich browser. CPU is single core with HT to give 2 cores.
[https://linuxhint.com/top_lightweight_web_browsers_linux/](https://linuxhint.com/top_lightweight_web_browsers_linux/)

---

### Post by jankohrasko142 on 2020-10-27
Thank you. I tried almost of them (except netsurf I could not install) and with all of them the CPU both threads were again at 100%.
Anything else I could optimize in the OS please ?

---

### Post by Tommy on 2020-10-29
I have a similar Acer Aspire One netbook and was unable to run most things until I upgraded from 1 GB RAM to whatever its maximum was (2 or 3 GB; I no longer recall). I also installed a SSD (solid state drive) and used zram to more efficiently use the minimal RAM.

I got the netbook working, and I really like the size -- very portable! But it's a great struggle to use it for much because of its weak processor and limited RAM.

---

### Post by mikewhatever on 2020-10-29
Intel Atom N270 @ 1.60GHz was not a speed demon when released in 2009, but by now, coupled with 1GB of RAM, it is pretty much obsolete. 
With an average score of 175, it is about eight times slower then  Intel Celeron N4000 @ 1.10GHz.
[https://www.cpubenchmark.net/cpu.php?cpu=Intel+Atom+N270+%40+1.60GHz&id=614](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Atom+N270+%40+1.60GHz&id=614)
[https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+N4100+%40+1.10GHz&id=3239](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+N4100+%40+1.10GHz&id=3239)

Firefox is multi-process now, same as most browsers, and probably overwhelms that CPU completely. ZRAM, mentioned above, would further increase CPU usage because of compression and decompression. There are optimizations you could do, but they won't make a lot of difference.
There isn't much you can do here.

---

### Post by geofftf on 2020-11-01
100% CPU utilisation is not a problem in itself. The CPU is there to be used, and you want the fastest response possible. Your processor is very slow by modern standards. It is not much faster than the processor on the $5 Raspberry Pi Zero. It does have twice as much RAM as the Zero though. The Zero is rubbish loading modern websites (using Chromium), but it gets there eventually. I assume that you are running the 32 bit version of Xububtu 18.04, which will soon be unsupported. You could try loading Raspberry OS. It might be fun to try, but it will not be fast on the web.

[https://projects.raspberrypi.org/en/projects/install-raspberry-pi-desktop](https://projects.raspberrypi.org/en/projects/install-raspberry-pi-desktop)

---

