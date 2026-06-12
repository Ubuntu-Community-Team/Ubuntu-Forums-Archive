---
title: "USB 3.0 external disk not working"
date: 2014-10-31
forum: Desktop Environments
---

### Post by alberto666 on 2014-10-31
I bought a few months ago a Seagate 3 TB external drive, USB 3.0, it is working good with my windows and Mac OS X, but when I login into my Ubuntu 14.10 it does not properly detected.

I tried to see if getting detected in

    fdisk -l (doesn’t show up in the list)

Using lsusb it shows up

    lsusb 

Bus 001 Device 006: ID 0bc2:a013 Seagate RSS LLC


Every time I connect it to a new USB port, it works. When changing to an already connected USB port the problem described above. Problem? All the ports have been used at least once.
I had this problem in previous versions and still have it in Ubuntu 14.10.
In USB 2.0 ports it works.
No problem with a different USB3.0 disk.

Any clue?

---

