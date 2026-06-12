---
title: "ATI Video Problem (and Internet Problem"
date: 2006-03-24
forum: Desktop Environments
---

### Post by Yimmy on 2006-03-24
OK, I've seen the solution for my ati video problem with x server not starting on my laptop.  The problem is I can't download the drivers, because I don't know how to get my internet up and running from the command line.  Help!

James

---

### Post by christhemonkey on 2006-03-24
If your connected to the internet and know the address then you can just
```
wget www.atidrivesrs.com/drivers/for/you
```
Although that is a pretty big If.

---

### Post by Yimmy on 2006-03-24
Yeah, the problem is I don't have my internet working.  I need to get my wireless card enabled.  It was easy on my old dell to do it from the graphic interface, but this noob is lost at the command line.  How can I get my connection working?

Thanks!

---

### Post by christhemonkey on 2006-03-24
What wireless card do you have?

---

### Post by Yimmy on 2006-03-24
The laptop is a Presario v2552us with integrated wireless.  All there site tells me is "54g™ 802.11b/g WLAN with 125HSM / SpeedBooster support"

---

### Post by Yimmy on 2006-03-24
It should be a broadcom.  I guess the bigger issue is with the ATI RADEON® XPRESS 200M IGP graphics, the x server won't start.  Is it a driver issue?  And if so I need to get my internet connection working to get the new drivers.  Any help is appreciated.  Thanks so far and in advance.

---

### Post by Yimmy on 2006-03-24
Found the solution here:
[https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresarioV2000Z?highlight=%28compaq%29%7C%28v2000%29](https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresarioV2000Z?highlight=%28compaq%29%7C%28v2000%29)

This will fix at least part of the problem on the Compaq Presario v2000 model with the ATI Radeon Xpress 200m video card.  If I notice any other issues with 3D acceleration I'll post it here.

James

---

