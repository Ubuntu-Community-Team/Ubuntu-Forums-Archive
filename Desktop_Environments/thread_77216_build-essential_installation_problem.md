---
title: "build-essential installation problem"
date: 2005-10-16
forum: Desktop Environments
---

### Post by natto on 2005-10-16
Hi,

When I try to install build-essential, I get prompted to insert the installation cd:

Please insert the disk labeled:
Ubuntu 5.10 _Breezy Badger_ - Preview amd64 (20050908)
in drive /cdrom/

However, I no longer have the CD, so I then click "cancel" and get:

Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?

I click "yes" and get:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu13_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu13_amd64.deb)
  

Is there a way to install this package from the repository?  

Thanks,

Brian

---

### Post by Hikaru79 on 2005-10-16
You can simply edit sources.list and comment out the CD line. Then it'll look in the net repositories by default :)

---

### Post by natto on 2005-10-16
Thanks for the quick reply!  That solved my problem.

---

