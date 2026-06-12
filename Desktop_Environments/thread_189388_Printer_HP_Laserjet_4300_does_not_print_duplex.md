---
title: "Printer HP Laserjet 4300 does not print duplex"
date: 2006-06-05
forum: Desktop Environments
---

### Post by brumen on 2006-06-05
I have installed a HP LaserJet 4300 printer on Ubuntu 6.06 
and have chosen the Duplex printing, but the printer 
does not print double sided, only single sided. Could it be 
a driver problem or an Ubuntu setup problem? 

Thanks a lot, 
Gorazd


P.s. Another question: Why is the cups deamon configured so that 
the port 631 is visible only from the local computer, but not from anywhere else. I had to add Port 631 in the conf file. It is not such a big problem, but I was really confused. On a local computer, nmap localhost gave port 631 as open, from everywhere else it was not visible. Where is this stated in the ubuntu documentation, that the setup has changed??

---

### Post by brickhead20 on 2006-06-09
I have the same problem with my HP DeskJet 990cxi. Anyone help?

---

### Post by neologisma on 2006-10-17
Same problem with HP Color LaserJet 2600n...](*,)

---

### Post by rishi000 on 2006-10-30
i think there just isn't any real support for duplex printing in linux. I have an hp laserjet 1320 and I can't get cups to print double-sided even when I use the driver from HP.

---

### Post by teich on 2007-10-02
I have having the same problem myself with Feisty and a laserjet 4300.  Is there a solution to this?  I feel bad killing all those trees unnecessarily.

---

### Post by amb.physis on 2007-10-26
I have the same problem (LaserJet 4250). I can print duplex in command line with
```

lpr -PLaserJet-4250 file.ps

```
and from xpdf. But when it comes to Kpdf or Kdvi or Kwhatever, it's very strange. I can select long edge binding, but then won't let me print because apparently in some driver settings the duplex appears as "not installed" and a dialog tells me there's a conflict...

Where are these driver settings? Why do I print duplex in xpdf and not in kpdf??

---

### Post by TheValk on 2007-10-26
I have an HP Laserjet 5850 on an ethernet network and it does print duplex OK.
I installed the HP Linux Imaging and Printing HPLIP from Synaptic.
Don't know if that fixes anything as I installed it before trying the printer after installing Gutsy.

---

### Post by froy02 on 2007-10-27
You might want to try to configure yout hp printers by using your browser. Type "http://localhost:631" and see if the printer dialog comes up.  If it does then you might be able to configure it.

For more info go to the hp support for linux at address below.
[http://hplip.sourceforge.net/install/step4/cups/index.html](http://hplip.sourceforge.net/install/step4/cups/index.html)

hope it helps...

---

### Post by amb.physis on 2007-10-29
It worked like a charm!

Where do you find out these things?? It's just that there are so many tricks... I never know where to look...

Thanks!

---

