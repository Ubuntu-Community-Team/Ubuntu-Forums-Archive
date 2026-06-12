---
title: "/var/log/messages strange error"
date: 2009-04-01
forum: General Help
---

### Post by tooker on 2009-04-01
Hi there,

I'm running a standard install of Ubuntu and when I tail /var/log/messages I get this:

Apr  1 15:36:10 cyclops kernel: [3179667.284482] acx: BUG: no free txdesc left
Apr  1 15:36:13 cyclops kernel: [3179669.779953] acx: BUG: no free txdesc left
Apr  1 15:36:15 cyclops kernel: [3179672.275414] acx: BUG: no free txdesc left
Apr  1 15:36:18 cyclops kernel: [3179674.770884] acx: BUG: no free txdesc left
Apr  1 15:36:22 cyclops kernel: [3179679.517744] acx: BUG: no free txdesc left
Apr  1 15:36:24 cyclops kernel: [3179681.011549] acx: BUG: no free txdesc left
Apr  1 15:36:26 cyclops kernel: [3179683.507044] acx: BUG: no free txdesc left
Apr  1 15:36:29 cyclops kernel: [3179686.002487] acx: BUG: no free txdesc left
Apr  1 15:36:31 cyclops kernel: [3179688.497957] acx: BUG: no free txdesc left
Apr  1 15:36:34 cyclops kernel: [3179690.993425] acx: BUG: no free txdesc left


This recurs all the way through the log.  Can anyone tell me what it means - and how i can fix this.

Kind regards
E

---

### Post by rolandrock on 2009-04-01
Tooker, you really need to provide a lot more info and demonstrate that you have done some work yourself.

Has this started happening recently?  What changes have you made to your system recently?  Have you googled for compatibility issues with your hardware (wifi card, video card, usb devices etc.)?  Have you modified your drivers somehow?  What version of Ubuntu?  Have you checked for errors in syslog? Have you tried googling the error and seeing of anything pertains to you?...etc.etc.

The obscurity of the error message (240 hits on google quoted) suggests an obscure cause (i.e. obscure hardware, dodgy software or strange user error).  This in turn implies that support will be difficult to come by so you will have to do some work yourself.

Here is a guide on reporting software problems written by one of IT's true global heroes, Simon Tatham, who should be knighted for his services to humanity.  You don't need to be so rigorous as he suggests when reporting general problems on a forum like this but, for Tathams's sake, give us _something_ to work with please!

[http://www.chiark.greenend.org.uk/~sgtatham/bugs.html](http://www.chiark.greenend.org.uk/~sgtatham/bugs.html)

---

### Post by tooker on 2009-04-01
Yes, I have googled the error (obv.) - I think it might be something to do with my wireless card.
As I said in the original post I have had this error for some time.

Has anyone else had this issue?

---

### Post by rolandrock on 2009-04-01
Hmmm.

Try using using lspci to find name of wireless hw and google for correct drivers or workarounds.

E.g. on my eee:

lspci |grep -i wire
01:00.0 Ethernet controller: _Atheros Communications Inc. AR242x_ 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by tooker on 2009-04-01
Thanks, i'll give this a go.

---

