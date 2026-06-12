---
title: "SD card support?"
date: 2005-10-30
forum: Desktop Environments
---

### Post by djst on 2005-10-30
In my Dell Inspiron 6000, I have a SD-card reader. When I insert a normal USB flash drive, it automatically mounts and pops up on my desktop. However, when inserting SD-cards, nothing happens. How do I mount SD cards and how can I make it automatic?

---

### Post by djst on 2005-11-03
No one knows how to mount an SD memory card? Then this should be added to my Dapper wishlist... :???:

---

### Post by lateo on 2005-11-12
hello,
is your sd-card reader/writer recognized by ubuntu?
i'm interested in GP2X so i'd like to be 'sure' sd-card will work with ubuntu before i buy this 185€ toy ;-)
thx

---

### Post by hw-tph on 2005-11-12
A lot of SD card readers and multi-type card readers will not work under Linux because they are "dumb" devices, requiring uploaded firmware in to be usable. In the case of a lot of notebook/laptop computers (like the HP/Compaq R3000/zv5000/nx9105 laptop series) decrypted firmware is not available and the device requires decrypted firmware (the Windows driver support program decrypts the encrypted firmware and uploads it to the device). Snail-mail Dell and ask them to open their stuff.


Håkan

---

### Post by Nu-Buntu on 2005-11-12
I have a USB SanDisk multi card reader, and it works perfectly with my SD cards from my Digital Camera. Therefore, I don't think it is an SD issue, but rather an issue with Ubuntu detecting your SD card reader slot.

---

### Post by hw-tph on 2005-11-12
Ah, yes. Sorry about that. I was referring to built-in card readers. Perhaps I should have been more clear about that.


H&#229;kan

---

### Post by djst on 2005-11-29
My SD card reader is built-in. How can I tell if Ubuntu detects it or not?

---

### Post by Copter on 2005-11-30
got the same problem on LG GS50 laptop with built-in card reader. when i insert SD card _nothing_ happens :/

---

### Post by metasyntax on 2005-11-30
You have 3 possible problems.

1) The card reader is not being detected as a USB device

2) The card reader is detected, but dosen't send events when a card is inserted so it dosen't automount

3) the card reader is not a USB device

in the case of #3, you are SOL as there is NO open source SD/MMC stack because the spec does not really allow it (you can google for an article on it)

In the case of #2, you can install "usbview" which should show you all the usb devices attached to your computer.  As well, you can open a terminal and "sudo tail -f /var/log/messages" then put the SD card in and see if there is something in your messages file.

for #1 you'll have to do some research, start at [http://www.linux-usb.org](http://www.linux-usb.org).  Then try google as well.

HTH,
meta

---

