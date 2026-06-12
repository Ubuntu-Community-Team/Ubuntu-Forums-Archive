---
title: "Grub will not auto start anymore"
date: 2007-03-25
forum: Desktop Environments
---

### Post by ruialexbarbosa on 2007-03-25
Hi,

when I start up my pc, I usually get a message saying Ubuntu will start in 8...7...6...5... seconds, and then it starts. This is not happening anymore. It will not auto start.

I have to manually press "ENTER" otherwise it will not start.

Can anyone help me with this?

Thanks

---

### Post by adam.tropics on 2007-03-25
Did you edit your /boot/grub/menu.lst  by any chance? Anyway, if you go into that file and look through, it's very well commented, you can change timings and autostart etc.

---

### Post by SuSUntu on 2007-03-25
Did you do anything that may have modified the /boot/grub/menu.lst file? Make sure that the last line of this menu.lst section

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout		8**

```

is not commented out. If it is, "uncomment" it by removing the #.

If you indeed have an active timeout value set, and your still having this issue, check this Bug Report:

[http://savannah.gnu.org/bugs/?func=detailitem&item_id=14620#options](http://savannah.gnu.org/bugs/?func=detailitem&item_id=14620#options)

Turns out, it could be a keyboard issue.


EDIT:

Sorry Adam.Tropics about partially duplicating your answer. This is the second time in 24 hours I've had to apologize for that. I need to learn how to type faster and/or learn how to stay focused instead of getting easily distracted. :)

---

### Post by adam.tropics on 2007-03-25
> **SuSUntu said:**
> 
If you indeed have an active timeout value set, and your still having this issue, check this Bug Report:

[http://savannah.gnu.org/bugs/?func=detailitem&item_id=14620#options](http://savannah.gnu.org/bugs/?func=detailitem&item_id=14620#options)

Turns out, it could be a keyboard issue.


EDIT:

Sorry Adam.Tropics about partially duplicating your answer. This is the second time in 24 hours I've had to apologize for that. I need to learn how to type faster and/or learn how to stay focused instead of getting easily distracted. :)

No worries, I do it all the time. And btw, that is one bizarre bug!

---

### Post by ruialexbarbosa on 2007-03-25
Sorted!

I have a wireless keyboard, so I use a second keyboard just to choose OS and that kind of thing. I had something on top of that second keyboard, and it was pressing a couple of keys, thus, not letting ubuntu start automatically.

Anyway, it's sorted now. Thanks for helping.

---

