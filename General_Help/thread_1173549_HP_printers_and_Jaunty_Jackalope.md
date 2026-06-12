---
title: "HP printers and Jaunty Jackalope"
date: 2009-05-29
forum: General Help
---

### Post by HippieDave on 2009-05-29
Ubuntu 9.04 immediately recognized my HP 3030 Laserjet printer, and prints fine. However, I have two issues I need to resolve:

1. For windows, HP had a "Tool Box" program which allowed you to manage the printer settings, including fax settings, from the PC. ( I need the faxes to be received on the PC, as I did w/ Windows.) But I can't find the equivalent software for Ubuntu 9.04. Any suggestions?

2,  Under Windows XP, I have the HP 3030 set as a shared printer on our home wireless network, so my wife can print from her office to the printer, which is located in my office and hardwired to my PC. Where can I find out how to set up this same shared printer situation in Ubuntu?

---

### Post by pytheas22 on 2009-05-29
1. Open a terminal from the Applications>Accessories menu and type:

```
hp-toolbox
```

I think this is what you're looking for.

If you receive an error message about lack of GUI support when trying to launch hp-toolbox, it's probably because you're missing the python-qt3 package.  You can install it by typing:
```

sudo apt-get install python-qt3
```

Then try launching hp-toolbox again.

2. I don't have any experience setting up something like this, but I think [this page]("https://help.ubuntu.com/8.10/serverguide/C/samba-printserver.html") describes what you need to do.  samba is Linux's implementation of the Windows file-sharing protocol; I assume that's what your wife's computer uses to connect to the printer via your machine.

---

### Post by HippieDave on 2009-05-30
Many thanks.  I'll work with that and see what happens.

---

### Post by chocobanana on 2009-05-30
What you're probably looking for is hplip

Just look for the hplip package in Synaptic :)

---

### Post by HippieDave on 2009-05-30
OK. I installed Samba on my Ubuntu PC and the printer is set as "shared".  I had my wife's windows XP look for and install a new printer, and it found the printer, which it recognizes as" Ubuntu HP 3030" and "installed it" -- all on its own using the Windows install printer wizard.

BUT... we can't print to it. Windows apparently "sees" it but says "Access denied. Unable to connect."

ADDENDUM:  Situation is still as above, but despite the PC saying "access denied, unable to connect", it is actually printing just fine. Go figure.
I found a very clear and helpful description of how it_ should_ sork at [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP) . However, my wife's windows refused to accept the process described there. Ah well.  Might work for somebody else.

---

