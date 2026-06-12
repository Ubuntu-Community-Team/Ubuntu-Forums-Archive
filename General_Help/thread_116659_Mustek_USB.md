---
title: "Mustek USB"
date: 2006-01-13
forum: General Help
---

### Post by mendy on 2006-01-13
I have found alot of confusion with postings regarding scanner problems, so I will explain to all how I got my Mustek 1200 UB to work. It probably applies to all scanners as well.

First, make sure you  have libusb installed.

Then go to [http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/) and find your scanner. If the *usb file is in blue, download it, and put it into 
/usr/share/sane/gt68xx.

Next, make sure the file /etc/sane.d/dll.conf has a line gt68xx in it, uncommented.

You can comment all the other lines, even if you see your scanner there.

That's it, let me know if it worked.

---

