---
title: "Dell Mini 9, Ubuntu &amp; Gparted! PLEASE HELP!!!"
date: 2009-07-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by darshanpatel09 on 2009-07-20
Hi,

Having a very big dilemma at the moment, I have a mini dell 9 which had ubuntu installed on it and it just died on me...no response just a blank screen.

I have booted up gpated from my usb and it shows i have a STEC PATA 8GB but I cannot use the mount feature or I cannot format it I cannot do nothing at all, I have used many tools via USB and nothing!

How can I reformat this bloody drive and reinstall ubuntu on this machine!

Thanks

---

### Post by ugm6hr on 2009-07-20
Perhaps it has just died, as you say.  A hardware failure will mean it won't work.  Best to send it back under warranty.


If you are desperate to try something...

If you boot from USB, you can try and wipe the HD and start again.

shred is worth trying.

```
sudo shred -vfz -n 1 /dev/sda1
```

After it gets past 3%, use Ctrl+C to stop.  Then try installing fresh.

Might work, but not hopeful.

---

