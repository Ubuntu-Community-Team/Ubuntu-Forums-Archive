---
title: "Boot Issue in Jaunty (reg timeout...)"
date: 2009-05-29
forum: General Help
---

### Post by hikewithmike on 2009-05-29
I finally perfomed a dual boot on my desktop with 9.04 by following the graphical instructions on [this website]("http://http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm").

At first everything went well, I shrinked the hard drive in Vista, and then booted from a USB drive to install Ubuntu.  I have it running as the parent operating system, so GRUB is in control.  After a day, the boot starting taking longer, and this is where my confusion lies...

...it will reach the splash screen and the Ubuntu login will have the load stats bar going back and forth below, but will not "fill in".  Instead, it will go to a black screen and text will start scrolling through with this

[a serious of numbers]...FW host 15 set PHY reg timeout ... it will keep scrolling, and the numbers on the left will increase in value usually till about 120, then it slow, spits out more text, and starts?

I haven't a clue what the issue might be, and sorry for my lack of expertise if a left out any helpful information.  I wanted to dual boot because I like Linux, it runs better than Vista, so I am at the bottom of a learning curve when it comes to command interface and what not.

Thank you ahead of time for any help

---

### Post by hikewithmike on 2009-05-30
Bump.

---

### Post by VMC on 2009-05-30
> **hikewithmike said:**
> I finally perfomed a dual boot on my desktop with 9.04 by following the graphical instructions on [this website]("http://http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm").

... it will keep scrolling, and the numbers on the left will increase in value usually till about 120, then it slow, spits out more text, and starts?



That outside link is broken.

When you say "starts", then does Ubuntu completely boot us ready for use?

We need more information. From Ubuntu, go to the Terminal (Applications > Accessories > Terminal), and type the following:

```
sudo fdisk -l
cat /boot/grub/menu.lst

```

---

