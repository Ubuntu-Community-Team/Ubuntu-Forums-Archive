---
title: "Grub Problems"
date: 2008-11-09
forum: Desktop Environments
---

### Post by sauce345 on 2008-11-09
I feel like this should not be that hard but am having trouble and no real good luck on the forums.  My problem is that i just cloned a hard drive containing hardy and vista on it from a small hard drive to a much larger one.  I have done this many of times with windows at my work.  Anyway i need to reinstall grub but cant seem to figure it out.  Everything i have read says to boot to a live cd and use sudo grub method.  Well my computer does not boot the live cd for some reason, i had to install using the alternate disk which was no big deal.  No luck with the rescue function on the alternate either.  When i get in i hit reinstall grub and it just returns me to the main menu.  I tried executing a shell but could not use the commands recommended with the sudo grub method.

Anyways help!!!

---

### Post by phantomgunex on 2008-11-09
what command did you input???

---

### Post by phantomgunex on 2008-11-09
Did you configure your computer's bios to boot from the cd first???

---

### Post by sauce345 on 2008-11-10
sudo grub but it did not work. from their i would of ran:

sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit

This is what countless other posts recomend but i am not sure what terminal i can get to that will allow me to run these commands.  I cannot use the live cd.

Yes i have the bios information correct.  Just simply need a straight way to get the grub to just rewrite the MBR.

---

### Post by phantomgunex on 2008-11-10
hmmm it should work... give me a moment.

---

### Post by phantomgunex on 2008-11-10
Maybe you want to try to burn another live cd

---

### Post by phantomgunex on 2008-11-10
Hey maybe you wanna try booting with knoppix and then install grub

---

### Post by sauce345 on 2008-11-10
I do not think that is the problem because it has been an ongoing thing with my computer for a while and have used many different discs.  Their has to be a way to do it. This is linux for goodness sakes.

---

### Post by phantomgunex on 2008-11-10
Lol i am also not that experienced with ubuntu only been using it for about 7 months...

---

### Post by sauce345 on 2008-11-10
And my thread is dead.  :(

---

### Post by caljohnsmith on 2008-11-10
Have you tried the [Super Grub Disk]("http://www.supergrubdisk.org")? If your computer can boot the Super Grub CD, it can reinstall Grub to the MBR for you.

---

### Post by sauce345 on 2008-11-10
I have not, i actually got the grub to appear again and everything looks normal, except when i hit my latest kernel to boot from it goes like normal and then just hangs forever.  So i guess i will try to reinstall the grub again with the disc later tonight.  Hopefully i can actually boot.

---

### Post by sauce345 on 2008-11-11
Don't know if anyone would care but i figured out the reason it was not working.   At first it was definitely a grub problem but i did manage to fix that eventually. After know everything was good in the grub the computer would show the grub and everything looked normal it just hung. Then i realized after booting to an old kernel that their inconsistencies on the cloned drive that it was complaining about and would not allow itself to boot.  So now i am trying to clone with clonezilla instead of this older ghost i have on a live cd.

---

