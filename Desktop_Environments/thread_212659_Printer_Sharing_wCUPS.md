---
title: "Printer Sharing w/CUPS"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Freddie on 2006-07-10
For the last two months I have had printer sharing working perfectly on Ubuntu, that is, until the latest cupsys upgrade, which broke my /etc/cups/cupsd.conf file. So, I copied over a 'fresh' one from another Ubuntu PC and then tried to do:
```

freddie@chlorine:~$ sudo /usr/share/cups/enable_browsing 1
Error: cannot modify custom configuration

```
Which I had been told to do as a better way of sharing my local printer out to the entire network. I also get that same message when I do enable_sharing 1 and have no idea what is causing it.

Can anyone help me get printer sharing working?

Regards Freddie.

---

### Post by Freddie on 2006-07-10
Anyone have any ideas? As I am finding it really hard to live without printer sharing and have no idea what is actually wrong (and why an update broke my config file).

Thanks for all of your help.

---

### Post by drpaul on 2006-07-10
Have you tried setting up printer sharing with Samba? Works for me.

Paul

---

### Post by Freddie on 2006-07-10
No, this is because all of the computers on my network are Linux/UNIX, and so it is more efficient to use CUPS rather than SMB.

Regards, Freddie.

---

