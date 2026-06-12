---
title: "Dell Laptop drains battery within minutes."
date: 2012-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kundan Negi on 2012-06-08
Hey Guys!
    I use Dell Laptop and using Ubuntu as a dual boot. But while using Ubuntu my laptop battery drains within minutes as compared to 3 hours for Windows 7.I told it to some of my friends using Ubuntu and they said that install the Graphics Card Driver. Some said change ur laptop. But let me make it clear that my laptop is 10 days old with intel i5 processsor so there is no question of my laptop being outdated. I installed the Graphics Driver by updating Ubuntu. May be i am wrong in Graphics Card Driver selection.So Guys Please Help me as its annoys me when i have to charge the laptop within minutes frequently:mad:

---

### Post by david be on 2012-06-08
Can you give more information about your laptop?
Graphics Card driver might be the cause. What kind of card?

You could install powertop and run it from the terminal as root. It will give you information on power consumption. (Let the laptop run on battery for most information.)

---

### Post by Kundan Negi on 2012-06-09
Thanks David be for showing some interest in my problems.
I have Nvidia GeForce GT 525M Graphics card.Can u tell me is graphics card driver for this card available for Ubuntu.Please Help Guys!!!!!

---

### Post by TenPlus1 on 2012-06-09
It sounds like both graphics adaptors are running at the same time instead of just using one, that will definiately drain a battery quicker than most...  You could try this option to see if it lets you select between both adaptors:

[http://askubuntu.com/questions/134349/howto-fix-hybrid-graphics-in-ubuntu-12-04](http://askubuntu.com/questions/134349/howto-fix-hybrid-graphics-in-ubuntu-12-04)

Failing that you could install a tool called Jupiter that allows you to tinker with your laptops power management and turn certain things on/off in a bid to extend battery life:

[http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html](http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html)

---

### Post by Kundan Negi on 2012-06-09
Thanks a lot TenPlus1!!!!!
It really worked.My laptop now drains less battery and gets heated less.Bumblebee really worked.Its has proved to be Transformers Bumblebee for me.And again Thanks a lot to u TenPlus1 and to UbuntuForum!!!!!!!!!!:guitar:

---

