---
title: "Problems after GRUB2 update"
date: 2009-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by EvansFive on 2009-11-17
I have upgraded my Dell XPS 435mt to 9.10 64bit from 9.04 64bit.  It is dual booted with Vista 64.

I decided to do the upgrade from GRUB to GRUB2.

All seemed to go OK and after doing the chain loading stage I did the final stage to go to GRUB2 .

I have a couple of issues now.....

When I do a system restart (ie I want to boot either Ubuntu or Vista), I get the "GRUB Loading" heading, and then it just sits there for ages...and nothing progresses to display the GRUB2 menu.

I waited a while, but the only way I can get a GRUB2 menu is to power off the DELL and restart that way.

At power up, it comes up with "GRUB Loading", displays a message "error: no such device: UUID ?????" (I can't get the rest of message) and then displays the boot menu.

Does anyone know how to fix this GRUB2 restart problem please?

I don't want to get in the situation of not being able to boot at all....so I am very concerned about this issue.

Before I trash GRUB2 and "try" and go back to GRUB, I thought I would seek some advice first???

---

### Post by EvansFive on 2009-11-17
Is there anyone that can assist with this GRUB2 boot problem please?

OR...should I get rid of GRUB2 and go back to GRUB?

---

### Post by florus on 2009-11-18
Try doing an update as the first step:
sudo update-grub

---

