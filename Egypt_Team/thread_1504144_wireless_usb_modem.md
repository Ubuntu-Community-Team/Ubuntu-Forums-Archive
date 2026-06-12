---
title: "wireless usb modem"
date: 2010-06-07
forum: Egypt Team
---

### Post by runeedge on 2010-06-07
Salaam,
I will be in Egypt in a few weeks and am interested in getting a wireless USB dongle from Vodaphone or Mobinil.  I will only be in Cairo for a few days.  Then, I will go to the countryside for one month.

Thus, as I won't have much time to troubleshoot, I am posting here.  Does anyone here use wireless internet via a Vodaphone or Mobinil usb modem?  Are there any problems I might encounter?  Does it work?

I am using Ubuntu 10.04 Lucid Lynx.

Shuukran,
Tim

---

### Post by pytheas22 on 2010-06-07
I can't speak from personal experience at all, but googling "vodafone usb modem ubuntu" suggests that it should work well.  Mobinil seems to have less support.

---

### Post by TheHardDisk on 2010-06-07
> **runeedge said:**
> Salaam,
I will be in Egypt in a few weeks and am interested in getting a wireless USB dongle from Vodaphone or Mobinil.  I will only be in Cairo for a few days.  Then, I will go to the countryside for one month.

Thus, as I won't have much time to troubleshoot, I am posting here.  Does anyone here use wireless internet via a Vodaphone or Mobinil usb modem?  Are there any problems I might encounter?  Does it work?

I am using Ubuntu 10.04 Lucid Lynx.

Shuukran,
Tim


Hey Tim,

I can verify that the vodafone and mobinil and etisalat usb sticks DO work in ubuntu 10.04 Lucid Lynx without a glitch, as a matter of fact when you insert the stick you will get a pop up screen saying that it found a usb modem stick, you select the country, in this case Egypt, then it will give you three options, vodafone, mobinil and etisalat, select the one you will get, click ok and you're done, the modem will be connected and seen through the regular network manager on the taskbar as if you were connected via a wifi connection.

Also as an ADDED bonus if you want, vodafone actually have a linux client available if you want to be able to send sms via the stick or monitor upload/download activities such as the windows vodafone application does.

Just download [https://forge.betavine.net/frs/download.php/542/vodafone-mobile-connect_svn20090615_all.deb](https://forge.betavine.net/frs/download.php/542/vodafone-mobile-connect_svn20090615_all.deb)  and [https://forge.betavine.net/frs/download.php/490/usb-modeswitch_0.9.7_i386.deb](https://forge.betavine.net/frs/download.php/490/usb-modeswitch_0.9.7_i386.deb)

put both files on your desktop for example, then in terminal cd Desktop
and type sudo dpkg -i *.deb it will install both files, then under Applications/Internet you'll see vodafone mobile connect manager.

But just so you're aware, the default installation via ubuntu is PERFECTLY fine if all you want is to connect straight away and begin browsing.

Take care.

---

### Post by runeedge on 2010-06-08
TheHardDisk,
Thanks.  That's exactly what I was looking for.  :)
Tim

---

### Post by Pronco on 2010-06-09
You can install the latest version of usb-modeswitch via the universe repository using apt-get instead of getting the aforementioned package. However, I can't install vodafone-mobile-connect_svn20090615_all.deb due to unsatisfied dependencies, it does require two packages to be installed but they're not available and seems obsolete

---

### Post by Pronco on 2010-06-09
> **Pronco said:**
> However, I can't install vodafone-mobile-connect_svn20090615_all.deb due to unsatisfied dependencies, it does require two packages to be installed but they're not available and seems obsolete

These packages works at least for me. 
[http://www.betavine.net/repo/packages/ubuntu/Ubuntu.tgz](http://www.betavine.net/repo/packages/ubuntu/Ubuntu.tgz)

---

