---
title: "Blacklisted Driver"
date: 2007-12-21
forum: Desktop Effects &amp; Customization
---

### Post by sekinto on 2007-12-21
My card has been blacklisted. I would like to know if there is any development being done to fix this.

I just need to know what would be a better idea:
--- wait for the driver issues to be worked out
--- skip the blacklist check and hope it works fine

Please give me your opinions.

---

### Post by Sef on 2007-12-22
What kind of card do you have that is blacklisted?

---

### Post by sekinto on 2007-12-28
Radeon XPRESS 200M 5955

---

### Post by Forlong on 2007-12-28
Are you sure about that? 
What's the output of ```
lspci -vn | grep -i VGA
```

---

### Post by sekinto on 2007-12-28
01:05.0 0300: 1002:5955 (prog-if 00 [VGA])

---

### Post by Forlong on 2007-12-28
I'm sorry, you are right.

It's up to you. The open radeon driver is classified as not stable enough with your card (not your card in general, it would be totally fine to use Compiz with the "restricted" fglrx driver and Xgl).

I'd recommend trying out
```
SKIP_CHECKS=yes compiz
``` and if it's too buggy for you, just install the proprietary driver through* System &#8594; Administration &#8594; Restricted Drivers Manager* and afterwards Xgl: ```
sudo apt-get install xserver-xgl
```

---

