---
title: "Selling my mini -- restore?"
date: 2009-10-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sanubie on 2009-10-10
I'm trying to sell my Dell Mini 9. But I already have a bunch of data on it. I'd have to send whoever buys it log in details. How do I restore it to like it was when I first got it? I looked up installing the os over again, but it still makes me set up an account. The new owner should do all that. What should I do?

---

### Post by damis648 on 2009-10-10
You will want to do an OEM install. Upon booting the live cd or usb stick that you will be reinstalling from, highlight the 'Install Ubuntu' option and press F4. In the list that pops up, choose 'OEM Install'. By doing this, ubuntu will be installed with a user called 'oem' and a password you specify. Once finished, reboot the computer and log in as 'oem'. When you get to the desktop, open a terminal and type
```
sudo oem-config-prepare
```
and when that finishes, shut the computer down. When the purchaser reboots it, it will ask to set up an account.

---

### Post by sanubie on 2009-10-10
> **damis648 said:**
> You will want to do an OEM install. Upon booting the live cd or usb stick that you will be reinstalling from, highlight the 'Install Ubuntu' option and press F4. In the list that pops up, choose 'OEM Install'. By doing this, ubuntu will be installed with a user called 'oem' and a password you specify. Once finished, reboot the computer and log in as 'oem'. When you get to the desktop, open a terminal and type
```
sudo oem-config-prepare
```
and when that finishes, shut the computer down. When the purchaser reboots it, it will ask to set up an account.

Hey, thanks a lot!! Your directions were exactly what I needed. Now it's listed on ebay and awaiting a new owner. I won't post the link because that might be against policy. But it's on ebay bundled with a wireless mouse and an external DVD player/burner. Thanks for your help.

---

### Post by ugm6hr on 2009-10-11
> **sanubie said:**
> Now it's listed on ebay and awaiting a new owner. I won't post the link because that might be against policy. But it's on ebay bundled with a wireless mouse and an external DVD player/burner. Thanks for your help.

Feel free to post a thread in the Community Market.

---

