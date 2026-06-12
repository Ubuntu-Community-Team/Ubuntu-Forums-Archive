---
title: "Printer Driver - How do I change in 12.04"
date: 2012-09-02
forum: Desktop Environments
---

### Post by Geffers on 2012-09-02
I am running 12.04 on a laptop and an old computer running Hardy used as a printer, scanner and media server.

Before upgrading to 12.04 network printing was fine, now it states missing filter. Scanning on same device fine but not printing.

How on earth do I alter the driver as the properties show an incorrect model but I cannot fathom how to change it.

Using the system add/remove printers it finds the printer but doesn't give any option at configuration.

Any pointers appreciated.

Geffers

---

### Post by Geffers on 2012-09-02
> **Geffers said:**
> I am running 12.04 on a laptop and an old computer running Hardy used as a printer, scanner and media server.

Before upgrading to 12.04 network printing was fine, now it states missing filter. Scanning on same device fine but not printing.

How on earth do I alter the driver as the properties show an incorrect model but I cannot fathom how to change it.

Using the system add/remove printers it finds the printer but doesn't give any option at configuration.

Any pointers appreciated.

Geffers

Checking further it appears my Hardy server system is the one showing the incorrect driver, incorrect or not I've been printing to it happily for a few years so I'll have to resolve this somehow but there seems very little option to configure on this latest Ubuntu.

Meanwhile old LiveCD prints fine.

Geffers

---

### Post by kurt18947 on 2012-09-02
What model printer?

---

### Post by Geffers on 2012-09-03
> **kurt18947 said:**
> What model printer?

HP Multi Function printer scanner C5280

Geffers

---

### Post by kurt18947 on 2012-09-03
> **Geffers said:**
> HP Multi Function printer scanner C5280

Geffers

Thanks.  In looking around HP's site, it appears that HPLIP should work with your machine.  I just checked and HPLIP is not installed on my 12.04.  It used to be installed by default, guess it was left off due to space considerations to fit a CD.   It should be available via the software center or (my preference) Synaptic.   Here is a direct download from HP if you want to go that route.
[http://hplipopensource.com/hplip-web/index.html?](http://hplipopensource.com/hplip-web/index.html?)
I suspect this will work for you.

---

### Post by Geffers on 2012-09-03
> **kurt18947 said:**
> Thanks.  In looking around HP's site, it appears that HPLIP should work with your machine.  I just checked and HPLIP is not installed on my 12.04.  It used to be installed by default, guess it was left off due to space considerations to fit a CD.   It should be available via the software center or (my preference) Synaptic.   Here is a direct download from HP if you want to go that route.
[http://hplipopensource.com/hplip-web/index.html?](http://hplipopensource.com/hplip-web/index.html?)
I suspect this will work for you.

Had it installed, including the toolkit.

Tells me it cannot find a connected network device, HPLIP used to work fine with an earlier version of Ubuntu.

I suspect this may be a filepath issue rather than a missing file but version 12.04 doesn't appear to offer much for configuration options and of course HPLIP tells me no device installed.

Geffers

---

### Post by kurt18947 on 2012-09-03
I'm afraid I'm not much help with HP issues,  I'm better versed with Brother.

---

### Post by Geffers on 2012-09-04
> **kurt18947 said:**
> I'm afraid I'm not much help with HP issues,  I'm better versed with Brother.

Thanks for interest.

Geffers

---

