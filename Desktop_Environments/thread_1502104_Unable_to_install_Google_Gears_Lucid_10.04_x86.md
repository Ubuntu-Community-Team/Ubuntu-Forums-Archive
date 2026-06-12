---
title: "Unable to install Google Gears Lucid 10.04 x86"
date: 2010-06-05
forum: Desktop Environments
---

### Post by mangoHead84 on 2010-06-05
Hi,

I've just installed a fresh copy of Lucid Lynx 32-bit version on my laptop. The distro works great and I am especially thrilled with the wireless improvements. 

One of the only problems that I've run into so far has been that I've been unable to install Google Gears with Firefox. It downloads and tries to install the addon, but as soon as it tries, I get the error message:

"Google Gears could not be installed because it is not compatible with your Firefox build type (Linux_x86-gcc3)....." (screenshot attached)

The last time I tried to install Gears onto this laptop it was running 9.04 and had this same problem. When I tried installing Gears onto my desktop machine, which was also running 9.04, but was a 64-bit OS, it had no problem and worked fine. Is this a problem with the architecture? i.e. Does Google Gears require a 64-bit OS? Could it be something else?

Thank you

---

### Post by mangoHead84 on 2010-06-07
Figured out the problem. It turns out that Google only makes the 64-bit version of gears available through its website. So that when you try to install it through the regular Firefox Add On method, it claims that the architecture is wrong.

The fix which I've found is to install the package 'xul-ext-gears' which is gears packaged for Debian/Ubuntu. Hope this helps someone.

---

### Post by peterp77 on 2010-07-25
Thanks. I tried package 'xul-ext-gears' and it worked well.

---

### Post by m4lte on 2010-09-13
> **mangoHead84 said:**
> The fix which I've found is to install the package 'xul-ext-gears' which is gears packaged for Debian/Ubuntu. Hope this helps someone.

The package works fine for me too. Thanks a lot!

---

### Post by dfreemind on 2010-10-09
Excellent!! I've always had problems trying to enable this useful option and always same error.
Thanks a million!! It works well!!

---

### Post by nutsy.ben on 2011-02-16
Wonderful !!!

Sharing tips, for making an icon in your PC to your Ubuntu Panel use the following command:
"/usr/bin/firefox" "https://mail.google.com/mail/"

---

### Post by LordDelta on 2011-02-16
Oooh! I thought Google Gears was Windows Only atm, actually.

Cool to hear that its not. :)

---

