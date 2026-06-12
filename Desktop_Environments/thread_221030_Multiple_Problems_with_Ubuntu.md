---
title: "Multiple Problems with Ubuntu"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Dalton_Man321 on 2006-07-22
Hello,
I am having a few problems with Ubuntu. First of all I can't connect to the internet. The networking program detects the router (I'm using wireless), but it can't connect. Then I try to configure the interfaces.conf file, and after that Ubuntu won't boot up. It stops at "Configuring Network" or something. Someone please help. :(

-Dalton

---

### Post by Dalton_Man321 on 2006-07-22
Bump

---

### Post by jimmygoon on 2006-07-22
> **Dalton_Man321 said:**
> Hello,
I am having a few problems with Ubuntu. First of all I can't connect to the internet. The networking program detects the router (I'm using wireless), but it can't connect. Then I try to configure the interfaces.conf file, and after that Ubuntu won't boot up. It stops at "Configuring Network" or something. Someone please help. :(

-Dalton

How do you mean it detects the router... Ubuntu doesn't have anything to do with the router... are you saying that it detects the network? Is it encrypted? Anything special about it at all?

---

### Post by Dalton_Man321 on 2006-07-22
Yeah, it detects the network. It's encrypted though, but that's pretty much it.

---

### Post by srunni on 2006-07-22
Linux wireless support isn't that great. If you're using a USB wireless adapter as pictured below, it's most likely not going to work. It's ethernet, or waste hours trying to get it to work. But with ethernet, in many cases, its zero-config, like it was for me.

---

### Post by Dalton_Man321 on 2006-07-22
I use a PCI Card for wireless. Is there a better chance for getting it to work?

---

### Post by srunni on 2006-07-22
Yes, there's definitely a better chance, as you're not using USB, but it might take some time. Is your box a laptop or desktop?

---

### Post by Dalton_Man321 on 2006-07-22
It's a desktop.

---

### Post by srunni on 2006-07-22
Why do you use the wireless card then? Is it because your box is far away from your router and/or modem? If so, try to use an ethernet connection. You can get a 100 foot ethernet cable at [www.newegg.com](www.newegg.com) for $8.

---

### Post by Dalton_Man321 on 2006-07-22
I use wireless because my computer is a floor below my router. I can't use an ethernet cable because my family will trip over the cable, plus I'm broke. :(

---

### Post by srunni on 2006-07-23
Well, you could try to go through the ceiling.

---

### Post by mssever on 2006-07-23
First, your success will depend on the chipset in your wireless card. This may or may not be the same as the wireless card brand/model number. You can find it by issuing the following command from a terminal and looking in the product line for your card.
```
lshw -class network | less
```
Then search for instructions on making your specific card work. What type of encrption are you using? WPA? WEP (WEP is easily hacked)?

As far as your unbootable system goes, it may be vainly trying to connect to the internet. Leave it alone for five minutes or so before deciding that it's hung. Failing that, try booting into recovery mode--or even to the live CD. Of course, you'll want to undo whatever you did (for now, at least).

Also, when it comes to rebooting, save yourself some time while you're trying to troubleshoot your networking: don't reboot. You don't need to. Doing ```
sudo /etc/init.d/networking restart
``` will accomplish the same thing without making the rest of your computer unusable. Plus, if it's taking too long, you can hit Ctrl+C and cancel the restart.

---

