---
title: "linux won't boot after updating"
date: 2009-02-08
forum: General Help
---

### Post by mefistofeles666 on 2009-02-08
using ubuntu 8.04.2 on a toshiba.

I just installed all the updates and when i restarted it asked me for the user name and password as usual, but when I hit enter it went black and restarted itself, after the "ubuntu loading" screen the orange bar stops right at the end and after a minute it starts giving me and error over and over and over. it reads as follow

 doing wacom set up
(whole lot of crap that I can read bc it goes away very fast)

in
[ 56.some-numbers] ata1.00:status: {DRDY ERR}
[ 56.some-numbers] ata1.00: error: {UNC}
[ 56.some-numbers] ata1.00:exception Emask 0x0 SAct 0x0 SErr 0x0 action 0c0
[ 56.some-numbers] ata1.00:BMDMA stat 0x24
[ 56.some-numbers] ata1.00: CMD c:c0:7d/00:00:00:00:00/e5 tag 0 dma 4096 i


and then it keeps giving me the same lines nonstop.

any ideas? is there a way to fix it without losing my files?


thanks

---

### Post by utnubuuser on 2009-02-08
Hi -- Suppose you've tried getting  in through rescue mode at boot selection?
And you've tried > sudo dpkg --configure -afrom the rescue console?

---

### Post by mefistofeles666 on 2009-02-09
Right now I'm using kernel 2.6.24.21. all the other kernels seem to be working properly and 23 is the only one that gives me a problem.

when I tried recovery mode on 23, it still gave me the problem. I tried it on 21 and then I checked the option to use dpkg. it didn't do anything and said it didn't find the cd.

---

