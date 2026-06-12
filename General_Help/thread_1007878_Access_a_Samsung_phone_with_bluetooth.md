---
title: "Access a Samsung phone with bluetooth"
date: 2008-12-10
forum: General Help
---

### Post by W3ird_N3rd on 2008-12-10
I'm trying to access the storage on a Samsung phone with Bluetooth on Ubuntu Hardy 8.04 with a Sweex BT202 USB adapter. So far, it's not going well.

I've disabled all security and made the desktop trusted on the phone and the phone trusted on the desktop. Installed the "bluetooth", "gnome-bluetooth" and "gnome-vfs-obexftp" packages. If I right click the BT icon and select "send file", I can perfectly send a file from the desktop to the phone at a very fast 34 KiB/s no matter how close the phone is to the adapter. Even so, I would be happy if I could access the files on the phone at that speed.

But I can't. When I select "browse device" from the BT icon and select the phone, I eventually get a nautilus that sometimes shows the / from the phone. But when I select any folder, I get:

> Kan "obex://[DE:AD:BE:EF]/Geheugenkaart" niet weergeven.
Fout: Another operation in progress
Kies een andere weergavemethode en probeer het opnieuw.
Roughly translated:
> Can't display "obex://[DE:AD:BE:EF]/Geheugenkaart".
Error: Another operation in progress
Choose another display method and try again.
In case I do not get the / I get this error right away.

dmesg has nothing to say, I only saw a "bridge firewalling registered" but I guess that's probably not even related to this problem.

I'm lost.

---

