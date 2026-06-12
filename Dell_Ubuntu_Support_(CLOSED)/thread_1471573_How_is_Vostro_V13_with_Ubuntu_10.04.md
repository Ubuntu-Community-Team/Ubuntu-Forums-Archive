---
title: "How is Vostro V13 with Ubuntu 10.04?"
date: 2010-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bubblehead74 on 2010-05-03
I am thinking to buy Vostro V13 with Ubuntu 9.04, but only if it works with 10.04. Anybody has this combo?

---

### Post by gomab2k4 on 2010-05-04
It works great! I have the Latitude 13, which is pretty much one in the same. The only problem that I do have however is with Ubuntu One, but I believe that it is an Ubuntu One issue, and not a 10.04 issue.

---

### Post by manzdagratiano on 2010-05-04
Currently running Vostro V13 with Karmic; formatted Dell's 9.04 including the OS partition. It is working perfectly! I have not tried putting Lucid on it following a grub2 issue I had while putting Lucid on my other laptop - a Sony VAIO VGNAR520E.

---

### Post by manzdagratiano on 2010-05-04
Just a word of minor caution though - when you install Ubuntu from scratch, the Broadcom STA drivers for wireless are not installed by default. To deal with that, you will have to connect the computer to the internet via ethernet, install bcmwl-kernel-source, and then reboot. Other than that there are no hiccups at all!

---

### Post by bubblehead74 on 2010-05-04
Thanks. Vostro V13 looks like a perfect fit for what I want. I was mostly afraid that the video will not work. The new kernel seems to be unforgiving with some video cards. Hopefully, these grub2 dual booting issues will get sorted out shortly.

---

### Post by quenbert on 2010-05-04
I've received my V13 4 days ago (Core2 Solo version) - 320 Gb hard disk. Machine is really great, rock solid aluminum case, great screen, ...

Only 3 drawbacks IMHO:
- battery life is ~3 hours, should be a little longer
- 320 Gb hard drive is a toshiba hdd, which is noisy: a strident fan noise from the bottom left corner of the keypad. Replaced it with a 250gb Samsung hdd, the laptop is now perfectly quiet.
- suspend to ram works flawlessly, but hibernate don't at all (hard power out on resume). Working on finding a solution ATM.

---

### Post by bubblehead74 on 2010-05-04
> **quenbert said:**
> Only 3 drawbacks IMHO:
- suspend to ram works flawlessly, but hibernate don't at all (hard power out on resume). Working on finding a solution ATM.

This is what I found in the release notes:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Hibernation%20may%20be%20unavailable%20with%20automatic%20partitioning](http://www.ubuntu.com/getubuntu/releasenotes/1004#Hibernation%20may%20be%20unavailable%20with%20automatic%20partitioning)

---

### Post by quenbert on 2010-05-04
bubblehead, thx for the tip, but my hibernate is know fixed (after a bit of googling): adding the no_console_suspend at the kernel boot cmd line fixed it!

Now everything I've tested is working:
* suspend2ram, hibernate (with the no_console_suspend option),
* ethernet
* wireless (but with closed source wl broadcom STA driver, b43 open source version gives strange behaviour, will retry it in the future)
* bluetooth
* sound
* webcam
* video (intel gma driver) and vga out
Not (yet) tested:
* express card and memory card reader

---

### Post by bubblehead74 on 2010-05-04
OK. It is ordered. Now I have to survive the wait. =P~

---

### Post by viniosity on 2010-05-08
To me the V13 is almost perfect on 10.04.  Two flaws:

1. Two finger scrolling doesn't work on the Synaptics trackpad.  I've tried just about everything I can but it's no dice.  If somebody's got it working I'd love to hear about it.

2. Laptop suspends when the lid is closed but doesn't resume on lid open until I touch the power button

#2 is minor.. but #1 is driving me nuts.

---

### Post by mervinb on 2010-05-10
For those who are happy with 10.04 on the V13, is normal touchpad scrolling (right edge vertical scrolling) working? I cannot get it to work. I am under the impression that the V13's touchpad is not recognised as a Synaptic device, and so it emulates a mouse only.

---

### Post by ptocquin on 2010-05-10
Hi all,

I have 2 problems running 10.4 on my Vostro V13 :

1. Shutdown, suspend or hibernate do not work. The laptop always re-starts or awakes immediately.
2. The scrolling function of the touchpad doesn't work.

Any ideas ?

---

### Post by keptang on 2010-05-17
I got the Latitude 13 with SSD and the Intel wireless (draft N), everything is working perfectly fine in Lucid, 64-bit of course!
I can really recommend the Vostro V13 / Latitude 13

---

### Post by topdownjimmy on 2010-06-24
> **manzdagratiano said:**
> Just a word of minor caution though - when you install Ubuntu from scratch, the Broadcom STA drivers for wireless are not installed by default. To deal with that, you will have to connect the computer to the internet via ethernet, install bcmwl-kernel-source, and then reboot. Other than that there are no hiccups at all!

For anybody experiencing problems with their wifi, I wanted to mention that after doing this I had to *shut down* my computer after activating the STA drivers, not just restart.

---

