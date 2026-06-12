---
title: "No &quot;backlight&quot; in XPS13 after installing the suggested packages (13.04)"
date: 2013-09-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by francesc-vilches on 2013-09-09
Hi all:

After one month using ubuntu 13.04 in a XPS13, the backlight has desapeared(brightness up/down) doesn't change anything.....even the buttons work.
I am pretty sure that this started after updating the suggested packages that included new kernel version......

I am trying to figure out how to proceed but I haven't found anything yet......
Anyone could help me to be able to see the screen a little bit "brighter"? I can use the laptop but it's pretty difficult to read it without enought brigthness.

Thanks in advance,
Francesc.

---

### Post by albandy on 2013-09-09
Open a terminal and type:
sudo gedit /etc/default/grub

Locate this line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
and replace it like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

then save the file and type in the terminal:
sudo update-grub

then reboot your computer to check if the trick works.

---

### Post by francesc-vilches on 2013-09-09
Thanks albandy. Unfortunatelly, it doesn't work. :(

---

### Post by Toz on 2013-09-09
There is an active [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/954661") for brightness issues on this laptop. What kernel version are you running? According to the posts at the end of that bug report, 3.8.0-30 is working (no need for the /etc/rc.local command if you are using it).

---

### Post by francesc-vilches on 2013-09-09
after typing "uname -r", it tells me ----> 3.8.0-30-generic

arrrrrrrgh!!  :guitar:

**If I boot with 3.8.0-29 it works fine** :P..............it's a good workarround until they fix it in further releases... 


P.S: In windows8, backlight is working.........I've tested just in case :P

---

### Post by Toz on 2013-09-09
Keep an eye on that bug report for more information on when/how it gets fixed.

---

### Post by francesc-vilches on 2013-10-06
Still same proble with new kernel 3.8.0-31 .........:-({|=

---

### Post by francesc-vilches on 2013-11-01
My BIOS  was set to **Load Legacy Option Rom: Disabled**

 As soon as I have set it to **Enabled**, now the backlight is working with last released kernels.

---

