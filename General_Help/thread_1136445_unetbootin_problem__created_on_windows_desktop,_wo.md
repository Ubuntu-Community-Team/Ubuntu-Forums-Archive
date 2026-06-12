---
title: "unetbootin problem : created on windows desktop, won't boot on netbook"
date: 2009-04-25
forum: General Help
---

### Post by baconrad on 2009-04-25
Hi,
I am trying to install easy peasy ubuntu on asus eee 1000, currently running xandros.

I used UNetbootin to create a disk image of easy peasy iso on usb flash drive on my windows desktop. I see files are extracted correctly. Then I plug flash into asus eee netbook. It will only boot from the hard drive. I went into the boot options and see that the usb drive is first and it even recognizes the label. My guess is it does not see it formatted as a system boot drive.

I may be missing something fundamental here as I am new to linux. Can I do what I am trying to do - install on windows desktop, boot on asus? Is it supposed to automatically boot from this drive?

Any help will be appreciated.

---

### Post by bennachie on 2009-04-25
In principle, everything you are doing sounds fine. Are you sure that you have specifically selected the relevant USB drive as your preferred boot device? When I hit "ESC" during the initial boot phase on my 701SD, I am presented with three options (the internal SSD, the external USB and the external SD card). I then have to identify one of these devices for that particular boot sequence.

---

### Post by dcstar on 2009-04-25
> **bennachie said:**
> In principle, everything you are doing sounds fine. Are you sure that you have specifically selected the relevant USB drive as your preferred boot device? When I hit "ESC" during the initial boot phase on my 701SD, I am presented with three options (the internal SSD, the external USB and the external SD card). I then have to identify one of these devices for that particular boot sequence.

Exactly, it is easier to just specifically select the boot device there because you have to set up any "new" USB device in the BIOS each time you start to use one.

---

### Post by baconrad on 2009-04-25
That worked! Thank you very much for taking the time to reply. It's booting right now.

---

