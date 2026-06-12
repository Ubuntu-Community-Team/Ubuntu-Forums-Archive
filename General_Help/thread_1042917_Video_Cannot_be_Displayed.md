---
title: "Video Cannot be Displayed"
date: 2009-01-18
forum: General Help
---

### Post by BakedBeans on 2009-01-18
alright so i finally went from windows to ubuntu and when i boot it up it goes through boot then video cannot be displayed and then directly to the login. I have ubuntu 8.10 and a dell 19" screen, anyways it bugs when that when i turn off and then when i also turn off my computer is doesn't support the video but it worked fine when i had it running off a live disk and not the hardrive that i installed it on. so i need help with fixing that

---

### Post by sully101 on 2009-01-18
So is the problem when your computer resumes from suspend or when you login? I think I need some more information. What video card do you have?

---

### Post by BakedBeans on 2009-01-18
its the splash screen before the login screen and the shutdown splash screen. that do not show up and says "cannot display this video mode" and the video card is a Radeon 9200pro family(ill get back to you on that it was a free computer) but its a p4 at 3.0, 1g RAM, and an asus mobo

---

### Post by sully101 on 2009-01-18
Can you login and open a terminal. If so type sudo dpkg-reconfigure xserver-xorg and reboot and see if that makes a difference. I have a 9600 Pro and am running the fglrx module with no trouble at all.

If you cannot get to a desktop. Press CTRL+ALT+F1 then login and run the above command and choose vesa as the driver, reboot and you should be good to go. 

Then click on Applications > System > Hardware Drivers and enable the ATI/AMD proprietary FGLRX graphics driver.

---

