---
title: "[SOLVED] Cant boot Ubuntu Desktop"
date: 2008-06-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ian@greenfigdesign.com on 2008-06-14
I have Ubuntu Desktop that i want to install on my Dell Inspiron 1720 but when i select to boot into Ubuntu without changing or effecting my current settings i get this error after the loading screen.

Buffer I/O error on device sr0, logical block 303446
Buffer I/O error on device sr0, logical block 303448
SQUASHFS error: s b_bread failed reading block 0x93a03
SQUASHFS error: unable to read page block 24e7117d

Any ideas why this is happening? 
These are my specs:
Intel Core 2 DuoT7700 2.4GHz
NVidia GeForce 8600M GT

Im going to buy a separate harddrive for my laptop because I dont want any problems with my current Windows installation. Do you think this might solve my problem or am i wasting my time doing that?

Thank you

---

### Post by gbrainin on 2008-06-14
sr0 is most likely your CD/DVD device.  My best guess is that you had an error in burning the Ubuntu CD, and should try re-burning it.  It's always a good idea to checksum the ISO after you download, and run the CD check after you burn.

---

### Post by 2words4uready on 2008-06-14
> **gbrainin said:**
> sr0 is most likely your CD/DVD device.  My best guess is that you had an error in burning the Ubuntu CD, and should try re-burning it.  It's always a good idea to checksum the ISO after you download, and run the CD check after you burn.

and also burn the image at the lowest speed possible to ensure it burn correctly is use infra recorder when burning and if i didnt set it to lowest speed i would always get an error just like the one your getting

---

### Post by ian@greenfigdesign.com on 2008-06-15
Thank you, that was the problem. I booted back into Windows and then mounted the ISO instead of burning a new CD. I then ran the umenu.exe and selected the option "Help me boot from CD".

This worked perfectly. Thank you

---

