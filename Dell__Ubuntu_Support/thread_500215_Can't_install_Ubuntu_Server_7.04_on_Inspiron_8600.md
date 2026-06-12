---
title: "Can't install Ubuntu Server 7.04 on Inspiron 8600"
date: 2007-07-13
forum: Dell  Ubuntu Support
---

### Post by harner on 2007-07-13
I am really big into Ubuntu Server 7.04 at work and I wanted to try it at home.  It works fine on a P4 w/HT test box but not on my laptop.  It's a Dell Inspiron 8600 w/a Pentium M @ 1.4Ghz, 512mb/ram and 32mb/Nvidia.

I go through the install and it looks good.  I reboot the box and I get an "Int 14:..." error!

After a lot of research, I realized no big deal something with the Ubuntu kernel.  I downloaded the desktop alternate CD and tried doing an install with that.  Once again, looked okay just took slightly longer to install.  it reboots and I get the same error.  I really want Ubuntu Server 7.04 on the laptop!  Preferably running Kubuntu.

---

### Post by kc2keo on 2007-07-17
Have you tried taking the quiet splash options off of the grub boot loader? I am saying this sou you can see the output from the boot process instead of seeing a pretty Ubuntu load bar. Although I think the server edition has it like that by default?

During boot does it fail when it tries to get to the X Server login screen? Do you use the X server?

Whats the full error?

Does the error come up on screen and nothing else is there but the error? 

Does the error come up immediately when you boot?

Do you even get to the boot loader?

--kc2keo

---

