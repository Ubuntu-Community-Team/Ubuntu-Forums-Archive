---
title: "New to Linux"
date: 2010-10-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Moirwinvail on 2010-10-25
so iv gotten kind of tired of windows, to be honest its more that i dont have the hundreds of dollars to buy a replacement disk for the operating system. anyway a friend of mine recommended me to try out Linux and i stumbled into a few Ubuntu video's/images.

my only issue is that i dont know which version would work best with my laptop, being a Dell: Inspiron 1501 void of ANY upgrades to the ram exc, and would appreciate any help in the right direction.


Thank you for your time.
Moir

---

### Post by TBABill on 2010-10-25
If the 1501 is fairly recent (last few years) then 10.04 would likely work well. Seems like most people with Dell laptops, me included, have a Broadcom wireless device. Those are working with 10.10 as well but a few have had to make driver tweaks to get theirs going. Mine worked fine in 10.10, but that doesn't mean yours will. But 10.04 is stable for the Broadcoms as far as I know, plus it is a long term support version that will be supported for 3 years and has lots of bugs worked out that 10.10 is now suffering from.
 
You can try both. Download them and put them on a LiveCD and give them a spin. The driver for many of the broadcom wireless cards is the STA driver. If you have a choice, read the details about both on the screen where it offers both and see which supports your model. If you have a choice of either, like my BCM4312, the STA driver seems to be the better one. But it has to support your model so that will be the deciding factor.
 
One note about Broadcom. If you install you will NOT have wireless access right away. You must plug into a router or modem and download the driver. The system will prompt you through it normally so all you have to do is give it a wired connection and go through the update process. During that process you should be prompted that proprietary drivers are available. Click the icon (it will be in the upper right of the screen on the upper panel) and enable the right driver for your card, then reboot. Should be all set indefinitely (or till you reinstall the operating system).

---

### Post by Gremlinzzz on 2010-10-25
Sites like these come in handy.
[http://ubuntuguide.org/wiki/Ubuntu:Maverick](http://ubuntuguide.org/wiki/Ubuntu:Maverick)

---

### Post by Moirwinvail on 2010-10-25
thank you both for your time, ill be checking out both versions to see how they do, i really appreciate your time and help.

---

### Post by gibbylinks on 2010-10-25
I'm running 10.10 on a 1501 at the moment. It runs great, but I have two issues/comments.

To boot it you need to include the "nomodeset" command in grub.

When booting from a live CD hold down the shift key after the BIOS screen to enter the grub menu.

Press E to edit the grub command line.

add the word "nomodeset" (without the quotes) after splash quiet

Then ctrl-x to boot.

If you don't do this it boots fine but you won't see any graphics.

Also you need to connect to the net using a cable to install the wireless drivers.

If you need anyore help don't hesitate to ask

---

### Post by Megaptera on 2010-10-25
I'm using the most recent Ubuntu LTS = 10.04 on a Dell Inspiron and it worked out of the box except for wireless which needed this very simple tweak:

[http://www.ubuntumini.com/2009/11/br...in-karmic.html](http://www.ubuntumini.com/2009/11/br...in-karmic.html)

---

### Post by dustinmarlowe56 on 2010-10-25
I own a 1501, and 64 bit ubuntu 10.04 works wonderfully. just when you install it you will need to be able to hook up to a wired internet connection in order to download the appropriate driver for the wireless card.

---

