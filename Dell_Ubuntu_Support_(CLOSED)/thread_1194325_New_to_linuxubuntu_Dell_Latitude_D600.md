---
title: "New to linux/ubuntu Dell Latitude D600"
date: 2009-06-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by einsteins on 2009-06-22
Hi all

I have installed ubuntu on my laptop inside of windows.
All went well but I cant seem to get the wireless networking to work at all.

I have followed a number of posted tutorials that have not worked...

Can anyone assist me with getting my wireless adapter to work.

THanks

einsteins

---

### Post by einsteins on 2009-06-22
Here is the wireless adapter found in my laptop...
Dell Wireless 1450 Dual Band WLAN MiniPCI Card

Thanks again..

---

### Post by ugm6hr on 2009-06-22
Connect with a wired cable, then go to System -> Admin -> Hardware Drivers

If you have tried some How-Tos, list them here.

If this doesn't work, give the output of:
```
lspci
lshw -class network
```

---

### Post by concerto on 2009-07-22
> **ugm6hr said:**
> Connect with a wired cable, then go to System -> Admin -> Hardware Drivers

If you have tried some How-Tos, list them here.

If this doesn't work, give the output of:
```
lspci
lshw -class network
```



Thank you!  I've been trying to fix my computer for hours and I never realized that I had to have it plugged in to eth0. 	:oops:

---

