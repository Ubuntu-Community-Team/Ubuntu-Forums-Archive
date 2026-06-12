---
title: "Wireless on Dell Mini 9 and Kubuntu 8.10"
date: 2009-03-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pipposanta on 2009-03-22
Hi,
I installed Kubuntu 8.10 on my Dell Mini 9 but I can't get wireless to work. Any suggestion?

Thanks in advance!!!

EDIT: I have a Broadcom BCM4312 which is a restricted driver. How can I install it without a connection?

---

### Post by ecrisfield on 2009-03-28
I have run into similar difficulties. My mini 9 is fine for now because it's still running the ubuntu 8.04 that came on it. But I'd like to upgrade it, possibly to 9.04 next month.

In the meantime, my Dell XPS 1530 is dual-booting to Kubuntu 8.10 and I had trouble with the wireless on it.

Fortunately, the install loaded the "restricted driver" for it.
I was able to activate the broadcom STA wireless driver under "Hardware Drivers" (Applications/System/Hardware Drivers) and after reboot I'm online.

I hope you get the mini on.

---

### Post by anjilslaire on 2009-03-28
After installing 8.10 on your mini 9, plug in a wired connection to your NIC and run all updates, then activate the Broadcom STA driver in the Restricted Driver Manager as noted.

---

### Post by ecrisfield on 2009-03-28
I don't have a wired connection, so when I can't get a machine online I have to use another computer whose wireless is working to pull the necessary files, then use a thumb drive to move them to the offline one.

Does anybody have the procedure worked out for downloading the restricted driver onto a USB drive and then installing it?

---

### Post by anjilslaire on 2009-03-28
well, when I installed 8.10, the wireless worked without problem, and I was able to download the restricted driver without needing the wired connection. Driver-wise, the functionality should be the same regardless of which desktop you're using, KDE4 or Gnome.

On a mini 9, you should at least get basic wireless connectivity without additional drivers. Try setting your wireless AP to unsecured and make sure you have your SSID correct.

---

