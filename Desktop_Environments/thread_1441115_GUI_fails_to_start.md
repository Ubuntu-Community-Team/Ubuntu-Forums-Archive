---
title: "GUI fails to start"
date: 2010-03-28
forum: Desktop Environments
---

### Post by Cavs23 on 2010-03-28
I have already browsed the internet and checked the forum for my problem. No one seems to have the same issue that i do.

When I try to boot into GUI it comes up with the error

```

unable to open evdev device /dev/ipnut/device5 
NAME OF KEYBOARD HERE failed to start

```
It does that ten times and then throws up the error.

---

### Post by MichaelSammels on 2010-03-28
How are you booting into Ubuntu? Normally?

---

### Post by Cavs23 on 2010-03-28
I decided to just reformat and resinstall Karmic and reinstall things that I had.

But one issue. Installing PAE break my GUI again. I boot into the PAE version of my kernal and my cmd line keeps flashing and it takes forever to reboot because it catches every other key stroke it seems. The GUI fails to start at that point with no error. After I reboot and choose the non PAE version, I can then boot into gui. I am using the nvidia 185 driver.

---

### Post by Cavs23 on 2010-03-28
Solved. I had to install the PAE headers

---

