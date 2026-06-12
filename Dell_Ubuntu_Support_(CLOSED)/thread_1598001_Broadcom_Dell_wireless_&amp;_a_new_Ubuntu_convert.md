---
title: "Broadcom Dell wireless &amp; a new Ubuntu convert"
date: 2010-10-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jpullen88 on 2010-10-16
Hi,

Well I have been learning quite a bit about Ubuntu lately. I have been trying to figure out how to enable wireless on my dell inspiron 1318 laptop. I don't really know anything about ubuntu or how to do anything other than open the terminal and input commands into that (commands that other people tell me to input =/ ). I tried doing the STA driver found in sys -> admin -> additional drivers but it never worked. My wireless section hasn't ever 'found' any networks and it is showing a greyed out 'disabled.' Can somebody please help me? When i input ~$ lspci it displays my wireless as a BCM4312 rev 01. I really tried for two days now and I am totally stumped. I did figure out how to extract my paper (due monday =( ) from a .rar so hopefully that shows im trying. Thanks and please help. Just tell me if you need anymore info about my wireless card.

Thank you,
Jason

---

### Post by Megaptera on 2010-10-16
Hi,
This simple fix works on Ubuntu 9.10, 10.04 and 10.10. Don't worry that it says Dell Mini, and don't forget the re-boot. Hope it works for you as well:

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by Jpullen88 on 2010-10-16
> **Megaptera said:**
> Hi,
This simple fix works on Ubuntu 9.10, 10.04 and 10.10. Don't worry that it says Dell Mini, and don't forget the re-boot. Hope it works for you as well:

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

I followed the guide and it gave me > Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log when I click install the driver. Maybe I need to completely remove traces of old attempts? If so how do I do that or any other ideas?

---

### Post by Megaptera on 2010-10-16
Can you post that log here in case someone can help you fro here on ....

---

### Post by Jpullen88 on 2010-10-16
I cannot post it as its too long and gives me an error when posting it on here. Also, I'd like to add that for some reason I can now see networks but I am perpetually trying to connect to them. It never connects. Any ideas?

---

### Post by stalker145 on 2010-10-16
I just went through what sounds like this problem with my Dell 1764 and Ubuntu 10.10.

I followed the instructions listed above and found everything was already installed. I marked the **bcmwl-kernel-source** for complete removal, reinstalled when that was done, restarted, and am now enjoying wireless happiness.

Try it and let us know if that works...

---

### Post by aysiu on 2010-10-16
I have the same Broadcom card, and System > Administration > Additional Drivers annoyingly [does not work.](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/534824)

Using the computer you have that has a working internet connection, download these three files:
[http://mirrors.kernel.org/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-3ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-3ubuntu1_all.deb)
[http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)

Transfer them via USB to your Dell Inspiron

Double-click to install the *patch* file first.
Then double-click the *dkms* file.
Then double-click the *bcmwl* file.

Then reboot. Your wireless should work.

---

### Post by TBABill on 2010-10-16
That's odd that you both have that issue. I have the same card and it works every time on 2 different machines when connected via ethernet to download the driver. Is there a bug that inhibits it on some machines from working properly via ethernet?

---

### Post by anjilslaire on 2010-10-16
The blog post with the fix has updated for Maverick as well. If you connect via wire, youi can get the wifi drivers online:
[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html]("http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html")

---

### Post by Megaptera on 2010-10-17
> **anjilslaire said:**
> The blog post with the fix has updated for Maverick as well. If you connect via wire, youi can get the wifi drivers online:
[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html]("http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html")

Thanks for that link , I've added it to my bookmarks.

---

