---
title: "Ubuntu on Dell Mini 10"
date: 2012-09-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by HankSpank on 2012-09-18
I have a Dell Inspiron Mini 1010 and after instillation I get the all too well known black screen. I understand that this is due to a driver issue; my graphics chipset doesn't have an open source driver. I know that, after a bit of finnicking that you can get it working, however all of the guides are aimed at a more experienced user. Are there any step by step guides that you guys could point me towards? Is one of you willing to help me through this?

TL;DR: I'm a noob and need a guide to get Ubuntu graphics working on a Dell Mini 10.

---

### Post by kaytrance on 2012-09-18
> **HankSpank said:**
> I have a Dell Inspiron Mini 1010 and after instillation I get the all too well known black screen. I understand that this is due to a driver issue; my graphics chipset doesn't have an open source driver. I know that, after a bit of finnicking that you can get it working, however all of the guides are aimed at a more experienced user. Are there any step by step guides that you guys could point me towards? Is one of you willing to help me through this?

TL;DR: I'm a noob and need a guide to get Ubuntu graphics working on a Dell Mini 10.

What do you mean by "black screen"? Console?

---

### Post by HankSpank on 2012-09-18
> **kaytrance said:**
> What do you mean by "black screen"? Console?

Totally black screen. Login screen sounds. Pressing ctrl+alt+F2 brings up console. As stated before, however, I am relatively new to Linux (this is only my 4th or so instillation and first on a laptop) and I am still not totally comfortable with it, but willing to learn.

---

### Post by HankSpank on 2012-09-18
More googling revealed [this]("http://askubuntu.com/questions/119889/how-to-boot-with-intel-gma500-poulsbo-graphics") page. Upon following the instructions the screen returned to its proper state. However this needs to be done every time I turn on the computer. Can I automate this process?

---

### Post by sanderj on 2012-09-18
> **HankSpank said:**
> Pressing ctrl+alt+F2 brings up console. 

In the console, what is the output of

```

lspci | grep -i vga

```

I believe the GMA500 is not supported, and/but there was a proprietary, binary driver for some specific kernel or Ubuntu version. So that might mean some older Ubuntu might work with that driver.

---

### Post by mikewhatever on 2012-09-19
Please see the Poulsbo wiki -> [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo). Step by step instructions are provided to work around the black screen.

---

### Post by kaytrance on 2012-09-19
> **mikewhatever said:**
> Please see the Poulsbo wiki -> [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo). Step by step instructions are provided to work around the black screen.
Also, if this helps, please mark thread as solved using thread tools above.

---

