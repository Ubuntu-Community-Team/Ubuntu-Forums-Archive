---
title: "Keyboard randomly stops working"
date: 2021-07-29
forum: Desktop Environments
---

### Post by vysero on 2021-07-29
Hey guys, I am getting increasingly frustrated as time goes by with this problem I am having. My keyboard seemingly randomly stops working. I might be typing code or writing a note or whatever it doesn't seem to happen at any specific time. Does anyone have any ideas about what the problem may be or how I might go about figuring out what the problem is?

I am on Ubuntu 18.04 and I have a wireless keyboard and mouse combo made by logitech the mouse has a label: M310.

---

### Post by QIII on 2021-07-29
Hello!

First things first:  16.04 is End Of Life (EOL) and is no longer supported unless you have specifically entered into an extended support agreement of some sort with Canonical.  That being the case, it is critical that you install a supported release or keep the machine disconnected from the web.  

You need to eliminate hardware failure.  Does the keyboard behave this way when used with another machine?  Does a different keyboard behave this way when used with this machine?

Again, more important still:  Your release of Ubuntu is EOL and it should not be exposed to the web.

---

### Post by SeijiSensei on 2021-07-29
Have you replaced the batteries in the keyboard yet?  Mine usually just ceases to function when the batteries run down.

---

### Post by Autodave on 2021-07-29
Any USB hubs hooked up?  They can pull the 5 volt line down and cause the keyboard not to function.  Try disconnecting every USB connected peripheral and see what happens.

---

### Post by philhughes on 2021-07-29
I've seen the same thing with a Logitech keyboard and mouse. Two suggestions:

- try to get the keyboard and mouse as near to the nano receiver as possible (use an extension cable if necessary) and line-of-sight
- USB 3 is known to cause interference on the 2.4GHz band used by these devices [1], so keep any USB3 memory sticks etc away for the nano receiver

If you search "Logitech mouse stuttering", you will see it is a common problem, and not exclusive to Linux.

[1] [https://www.intel.com/content/www/us/en/products/docs/io/universal-serial-bus/usb3-frequency-interference-paper.html](https://www.intel.com/content/www/us/en/products/docs/io/universal-serial-bus/usb3-frequency-interference-paper.html)

---

### Post by vysero on 2021-07-30
This is my mistake. I meant to type 18.04. I have corrected this mistake in the original post.

---

### Post by ActionParsnip on 2021-07-31
Tried a different keyboard or different USB port?

---

### Post by vysero on 2021-08-02
I have recently flipped my computer around s/t the business end (where the usb dongle resides) is facing me. I am hoping this will help.

---

### Post by Autodave on 2021-08-03
If that works, you can buy a 2 or 3 foot USB3 cable and return your PC to its proper rotation! :-)  The cable will allow you to move the receiver out front.

---

### Post by vysero on 2021-08-05
It hasn't happened since the flip. I am going to go ahead and assume the cause was the keyboards relative proximity to the dongle. Thanks guys.

---

