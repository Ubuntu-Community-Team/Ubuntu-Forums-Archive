---
title: "ubuntu 9.10 memory issue"
date: 2009-12-16
forum: Desktop Environments
---

### Post by saydemi on 2009-12-16
i have recently installed ubuntu 9.10 on my dell optiplex 170. i have 2GB ram installed on my system. the bios settings shows that the correct amount but when i look at the available memory  (top,free -m) is only shown 256MB. i have only ubuntu installed on my system. thanks.


:~$ uname -r
2.6.31-16-generic

top - 23:13:49 up 17 min,  2 users,  load average: 0.20, 1.04, 1.34
Tasks: 128 total,   1 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.6%us,  1.0%sy,  0.0%ni, 96.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    241960k total,   227192k used,    14768k free,      684k buffers
Swap:   706820k total,    36120k used,   670700k free,    42228k cached

---

### Post by sanderj on 2009-12-16
According to [http://docs.google.com/viewer?a=v&q=cache:UJhLH-qQY2EJ:www.dell.com/downloads/global/products/optix/en/spec_optix_170L_en.pdf+dell+optiplex+170+site:dell.com&hl=nl&gl=nl&sig=AHIEtbRMRVEyQm_fWHOOXMw2RzdpnGcoAw](http://docs.google.com/viewer?a=v&q=cache:UJhLH-qQY2EJ:www.dell.com/downloads/global/products/optix/en/spec_optix_170L_en.pdf+dell+optiplex+170+site:dell.com&hl=nl&gl=nl&sig=AHIEtbRMRVEyQm_fWHOOXMw2RzdpnGcoAw) you can indeed have up to 2GB RAM.


So: can you run the script check-my-hardware.py attached to post [http://ubuntuforums.org/showpost.php?p=8284040&postcount=11](http://ubuntuforums.org/showpost.php?p=8284040&postcount=11) . It will tell you everything about your memory

Usage:

```
sudo python check-my-hardware.py
```

Post the complete back here. Example of my output:

```
sander@quirinius:~/Downloads$ sudo python check-my-hardware.py 
[sudo] password for sander: 
OK, you're root
ANALYSIS:
Total of physical memory modules found 1024 MB in 1 memory module(s)
BIOS offers 1013 MB as usable
Memory seen by OS 993 MB
BIOS version 04/14/2009
CPU is PAE enabled
CPU is 32-bit, and not x86_64 enabled
OS is 32-bit
ADVICE:
Your physical memory is less than 3200 MB, and your system does not need special memory treatment
sander@quirinius:~/Downloads$
```

---

### Post by saydemi on 2009-12-16
i got the following output.

sudo python check-my-hardware.py 
OK, you're root
ANALYSIS:
Total of physical memory modules found 1024 MB in 4 memory module(s)
BIOS offers 246 MB as usable
Memory seen by OS 236 MB
BIOS version 01/21/2005
CPU is PAE enabled
CPU is 32-bit, and not x86_64 enabled
OS is 32-bit
ADVICE:
Your physical memory is less than 3200 MB, and your system does not need special memory treatment

---

### Post by Darth Lukan on 2009-12-17
Looks like somebody needs a BIOS update/fix.  Your BIOS at POST may be showing 2GB RAM, but it is only passing 256MB to your system as usable.  That BIOS revision is also showing as of 2005, check your hardware manufacturer to see if they have a more recent BIOS revision (they should).

---

### Post by sanderj on 2009-12-17
> **saydemi said:**
> i got the following output.

sudo python check-my-hardware.py 
OK, you're root
ANALYSIS:
Total of physical memory modules found 1024 MB in 4 memory module(s)
BIOS offers 246 MB as usable
Memory seen by OS 236 MB
BIOS version 01/21/2005


So:
Physically only 1024 MB of your 2GB is seen.
You have four memory chips (DIMMs) installed. Is that correct?
The BIOS only offers 246 MB to the OS.

I would do this:
check that your memory chips are compatible with your motherboard
update the BIOS to the newest version
check the BIOS for settings about your memory

HTH

---

### Post by weishigoname on 2009-12-22
ws@ws-laptop:~/Downloads$ sudo python check-my-hardware.py
OK, you're root
ANALYSIS:
Total of physical memory modules found 1024 MB in 1 memory module(s)
BIOS offers 886 MB as usable
Memory seen by OS 864 MB
BIOS version 03/04/2009
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit
ADVICE:
Your physical memory is less than 3200 MB, and your system does not need special memory treatment

I got problem in ubuntu 9.10-64bits,It is my computer memory always use too much,when I run for a while ,when I shut all my applications down ,memory still can not be free.even sometime, swap use 100%,there,my computer run slowly,and I have to restart my computer .that is why ?

---

