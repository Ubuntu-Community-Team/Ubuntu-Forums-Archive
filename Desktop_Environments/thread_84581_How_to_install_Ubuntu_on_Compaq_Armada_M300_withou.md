---
title: "How to install Ubuntu on Compaq Armada M300 without CDROM or Floppy?"
date: 2005-10-31
forum: Desktop Environments
---

### Post by Dan1el on 2005-10-31
Hi guys,

Yes, here is another one for you.

How do you install Ubuntu when the M300 is missing both CDROM and Floppy?

Ive got 2 laptops. The one that i wanna install Ubuntu on is fairly old. Ive got the first version of the BIOS, (v1.00).. Ive got a new external CD/DVD-rom drive using the USB-port on it which offcourse cannot be found once u reboot. Works perfect inside WinXP which i currently have installed on there for the moment.

I thought i had a couple of options here.

1. 
If I was to upgrade my BIOS, ((with latest file SP21036.exe), which will be very tricky though it needs to be done from a floppy-disc??), it will find my external CDROM and the rest is peace of cake. 

2. 
I would try and use the Ethernet mount option in the BIOS although ive never done it before. Does this by any chance require a server version software on PC nr2 to function as a Host/Server with data to install or what?

3. 
I try and use Partition Magic/Partition Boot Magic from within XP to create a mountable partition with the Ubuntu-livecd/Install CD or something on. 

4.
I take the harddrive out of the old laptop and put it into my current one, (which is up to date), and then run the installation cd and be prepare to reset all configurations once i put it back into the old one again?

Whats your suggestion?

Im lost with no answers, help anyone?

/Thx, Daniel.

---

### Post by mxyzptlk on 2005-10-31
well in my experience i suggest number 3 .

try to install from internet.

but you should enable in your bios the Option

boot from lan or ethernet or something like that.

i dont recommend the changing hardware option because the grub is going to 
fail on startup unless you decide not to install it.

and there´s another choice for you:

try to find out if you have in your BIOS the boot from usb device option. If so you will be able to boot from it and place your ubuntu disk in your external cd-rom

---

### Post by mxyzptlk on 2005-10-31
sorry it´s not 3 but 2 hehe

---

### Post by drubulvr on 2008-06-24
I know this is an old thread, but it was the first one I found before solving the problem and I wanted to update the "how"

[http://fernieville.wordpress.com/2008/06/21/no-cd-no-floppy-new-hd-old-computer-no-problem/](http://fernieville.wordpress.com/2008/06/21/no-cd-no-floppy-new-hd-old-computer-no-problem/)

Also, I suggest using XFCE on the Armada M300...gnome is ok, but XFCE is so much faster.

> **Dan1el said:**
> Hi guys,


Yes, here is another one for you.

How do you install Ubuntu when the M300 is missing both CDROM and Floppy?

Ive got 2 laptops. The one that i wanna install Ubuntu on is fairly old. Ive got the first version of the BIOS, (v1.00).. Ive got a new external CD/DVD-rom drive using the USB-port on it which offcourse cannot be found once u reboot. Works perfect inside WinXP which i currently have installed on there for the moment.

I thought i had a couple of options here.

1. 
If I was to upgrade my BIOS, ((with latest file SP21036.exe), which will be very tricky though it needs to be done from a floppy-disc??), it will find my external CDROM and the rest is peace of cake. 

2. 
I would try and use the Ethernet mount option in the BIOS although ive never done it before. Does this by any chance require a server version software on PC nr2 to function as a Host/Server with data to install or what?

3. 
I try and use Partition Magic/Partition Boot Magic from within XP to create a mountable partition with the Ubuntu-livecd/Install CD or something on. 

4.
I take the harddrive out of the old laptop and put it into my current one, (which is up to date), and then run the installation cd and be prepare to reset all configurations once i put it back into the old one again?

Whats your suggestion?

Im lost with no answers, help anyone?

/Thx, Daniel.

---

