---
title: "modem drivers"
date: 2010-09-25
forum: Desktop Environments
---

### Post by werkman2 on 2010-09-25
Im new here, so please excuse me if posted in the wrong sectionm
I have a hp laptop, installed ubuntu ver10.64, now my problem is that my 3g usb modem is detected as a usb flash storage device. I tryid every thing to make it connect to interned but invain.
Also my wifi is not working. Can any body please help me to make it work, or sent me instructions to [email]werkman2@gmail.com[/email] ?
My laptop is a 64bit system. Thx

---

### Post by tom4everitt on 2010-09-26
Hi, and welcome to the forum!

I only have a few general advices:
Connect the your laptop to internet via an ethernet cable so you can install all available updates. You should also check under
System->Administration->Hardware Drivers (the menu at the top left)
Sometimes there are proprietary drivers for wifi and 3g for your computer available there. It will only show you drivers that fit your hardware, so it will be easy to see if there's anything available. Note that you need to be connected to the internet for this service.

If that doesn't help you should try to find out the exact name of the hardware you're having problem with, so as to see if the question has already been answered. Otherwise other will be able help you easier if they know what hardware you've got (obviously). 

To find out what hardware you've got you can use the following commands (in a terminal).

```

lspci                           # Displays a list of detected hardware
lspci | grep Ethernet           # Displays only ethernet (internet) hardware
lspci -v | grep Ethernet -A 10  # Displays a more verbose list of ethernet hardware

```

If you need more detailed information, I would refer you to the "Hardware & Laptops" section. Start a new thread there if this doesn't help you.

---

