---
title: "Mini 9 suspend problem 9.04"
date: 2009-06-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by roberts3000 on 2009-06-04
I installed ubuntu 9.04 everything works great except I have an issue with suspend. When the laptop come out of suspend it has errors:

MMC: killing request for dead queue
btusb_intr_complete hci0 urb  failed to resubmit

The bluetooth I dont care about, it works fine connects back to my mouse every time.
The MMC is the problem. This only happens when a SD card is present. It re-mounts the card every time the lid is opened (come out of suspend) This is not good if I have a file open on the card.

I have tried Ubuntu, xubuntu, and netbook remix. same problem with all three.

Did not have this problem with the dell pre-load ubuntu 8.04.

Has anyone else seen this?

---

### Post by roberts3000 on 2009-06-04
update- I found this on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/272557](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/272557)

---

