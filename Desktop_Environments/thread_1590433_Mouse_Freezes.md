---
title: "Mouse Freezes"
date: 2010-10-07
forum: Desktop Environments
---

### Post by huedawg on 2010-10-07
Hello all :) I seem to have a small problem . When I boot into Ubuntu and login , after a few minutes my mouse freezes up . It's usb and I've checked the port to ensure that its working and it is . I have 10.04.1 ( 64bit) . Any suggestions would greatly be appreciated ..

---

### Post by JBAlaska on 2010-10-07
Try this: Immediately on booting, open a terminal and leave it open, go about your business and after your mouse freezes alt-tab to the terminal and type ```
lsusb
```- does the command complete or does it hang the terminal? if it completes, please post the output of ```
tail /var/log/messages
```

Also please post the output of ```
sudo xinput list
```

---

### Post by huedawg on 2010-10-07
> **JBAlaska said:**
> Try this: Immediately on booting, open a terminal and leave it open, go about your business and after your mouse freezes alt-tab to the terminal and type ```
lsusb
```- does the command complete or does it hang the terminal? if it completes, please post the output of ```
tail /var/log/messages
```Also please post the output of ```
sudo xinput list
```
Thank you! I'll do that as soon as it freezes and post back the output .

---

