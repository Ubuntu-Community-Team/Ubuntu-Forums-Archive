---
title: "Xubuntu fails to communicate with cups"
date: 2012-11-14
forum: Desktop Environments
---

### Post by ein anderer on 2012-11-14
Hi!

I use Xubuntu 12.10 and can't print. Cups is installed and running
```
status cups
cups start/running, process 3759

```The Web interface at localhost:631 is working as well.

But in the Settings Manager | Printers I get the message:
"Printing service not available. Start the service on this computer or connect to another server."
As a consequence I can't print in any applications since no printers show up.

Any help is very much appreciated!

Thanks,
Martin

---

### Post by rai4shu2 on 2012-11-14
From looking around, it seems like the fix is to go into System / Printing and Delete your printer. Then reboot and add the printer back.

---

### Post by ein anderer on 2012-11-15
At the moment I don't have a printer installed. 
Adding a printer in the cups web interface works fine - I just can't use it in any XFCE printing dialogues.

---

### Post by ein anderer on 2012-11-15
I have found the problem. For the record the problem was that in ~/.cups/client.conf contained a wrong port number. I am not sure how that happend, but changing it to
```
ServerName localhost:631
```
made it work again.

rai4shu2, thank you for your help!

---

